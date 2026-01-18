# WinPick.nvim

A Neovim plugin for quickly picking windows to focus by pressing letter labels displayed on them.

## Installation

### Using [lazy.nvim](https://github.com/folke/lazy.nvim)

```lua
{
  'pirey/winpick.nvim',
  config = function()
    require('winpick').setup()
  end
}
```

### Using vim.pack

```lua
vim.pack.add({ 'https://github.com/pirey/winpick.nvim' })
```

## Requirements

- Neovim 0.7.0 or later

## Usage

Call the `pick()` function to start window picking:

```lua
require('winpick').pick()
```

You can set up a keymap for easy access:

```lua
vim.keymap.set('n', '<c-w>p', require('winpick').pick, { desc = 'Pick window' })
```

When activated, letters will appear on each window. Press the corresponding letter to focus that window, or press the cancel key to exit.

## Configuration

The plugin uses these default options, which you can override by passing options to the `setup()` function:

```lua
require('winpick').setup({
  position = 'center',
  cancel_key = '<esc>',
  letters = { 'a', 's', 'd', 'f', 'g', 'h', 'j', 'k', 'l' },
  skip_buftypes = {},
  skip_filetypes = {'opencode_footer'},
  border = 'auto',
  padding = { x = 2, y = 0 },
})
```

## Options

| Option | Type | Description | Default |
|--------|------|-------------|---------|
| position | string | Label position: center, topleft, topright, bottomleft, bottomright, topcenter, bottomcenter | center |
| cancel_key | string | Key to cancel window picking | <esc> |
| letters | table | Letters for labels (extends automatically) | { 'a', 's', 'd', 'f', 'g', 'h', 'j', 'k', 'l' } |
| skip_buftypes | table | Buffer types to skip | {} |
| skip_filetypes | table | File types to skip | {'opencode_footer'} |
| border | string | Border style ('auto' uses vim.o.winborder) | auto |
| padding | table | Label padding (x: horizontal, y: vertical) | { x = 2, y = 0 } |
