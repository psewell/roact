<h1 align="center">Roact</h1>
<div align="center">
	<a href="https://travis-ci.org/Roblox/Roact">
		<img src="https://api.travis-ci.org/Roblox/Roact.svg?branch=master" alt="Travis-CI Build Status" />
	</a>
	<a href="https://coveralls.io/github/Roblox/Roact?branch=master">
		<img src="https://coveralls.io/repos/github/Roblox/Roact/badge.svg?branch=master" alt="Coveralls Coverage" />
	</a>
	<a href="#">
		<img src="https://img.shields.io/badge/docs-website-brightgreen.svg" alt="Documentation" />
	</a>
</div>

<div align="center">
	A declarative view library for Roblox Lua inspired by <a href="https://reactjs.org">React</a>.
</div>

<div>&nbsp;</div>

## Installation

### Method 1: Installation Script
* Download the latest release from the [GitHub releases page](https://github.com/Roblox/Roact/releases).
* Use the 'Run Script' menu (located in the Test tab) to locate and run this script.
* Follow the instructions in the installer

This installation script is generated by a tool called [rbxpacker](https://github.com/LPGhatguy/rbxpacker).

### Method 2: Filesystem
If building a Roblox place by importing scripts from the filesystem, copy the `src/roact` directory into your project and use a plugin like [rbxfs](https://github.com/LPGhatguy/rbxfs) to synchronize the filesystem into a Roblox place.

## Usage
# Roact
Roact is a declarative Lua view framework intended to mirror Facebook's *React* framework. It exposes a very similar API to React and implements nearly identical semantics.

## Hello, Roact!
This sample creates a full-screen `TextLabel` with a greeting:

```lua
local LocalPlayer = game:GetService("Players").LocalPlayer

local Roact = require(Roact)

-- Define a functional component
local function HelloComponent()
	-- createElement takes three arguments:
	-- * The type of element to make
	-- * Optionally, a list of properties to provide
	-- * Optionally, a dictionary of children. The key is that child's Name

	return Roact.createElement("ScreenGui", {
	}, {
		MainLabel = Roact.createElement("TextLabel", {
			Text = "Hello, world!",
			Size = UDim2.new(1, 0, 1, 0),
		}),
	})
end

-- Create our virtual tree
local root = Roact.createElement(HelloComponent)

-- Turn our virtual tree into real instances and put them in PlayerGui
Roact.reify(root, LocalPlayer.PlayerGui, "HelloWorld")
```

We can also write this example using a *stateful* component:

```lua
local LocalPlayer = game:GetService("Players").LocalPlayer

local Roact = require(Roact)

-- Create our component type
local HelloComponent = Roact.Component:extend("HelloComponent")

-- 'render' MUST be overridden.
function HelloComponent:render()
	-- createElement takes three arguments:
	-- * The type of element to make
	-- * Optionally, a list of properties to provide
	-- * Optionally, a dictionary of children. The key is that child's Name

	return Roact.createElement("ScreenGui", {
	}, {
		MainLabel = Roact.createElement("TextLabel", {
			Text = "Hello, world!",
			Size = UDim2.new(1, 0, 1, 0),
		}),
	})
end

-- Create our virtual tree
local root = Roact.createElement(HelloComponent)

-- Turn our virtual tree into real instances and put them in PlayerGui
Roact.reify(root, LocalPlayer.PlayerGui, "HelloWorld")
```

## License
Roact is available under the [TODO] license. Details are available in [LICENSE.md](LICENSE.md).