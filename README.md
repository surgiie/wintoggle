# wintoggle

[![CI](https://github.com/surgiie/wintoggle/actions/workflows/ci.yml/badge.svg)](https://github.com/surgiie/wintoggle/actions/workflows/ci.yml)
[![License](https://img.shields.io/github/license/surgiie/wintoggle)](LICENSE.md)

A bash cli that toggles a window in or out of the current active monitor.

## Dependencies

- `xdotool`
- `xprop`
- `pgrep`
- `bc`

## Install

Download script to machine where $PATH is available:

```bash
desired_version=main
install_dir="$HOME/.local/bin"
wget -P /tmp https://raw.githubusercontent.com/surgiie/wintoggle/$desired_version/wintoggle && chmod u+x /tmp/wintoggle && mv /tmp/wintoggle $install_dir/wintoggle
```

## Usage:

```bash

# searches for a process with "firefox" in its name (the more characters here the better as its a "contains" search) and toggles it in or out of the current active monitor
wintoggle --name "firefox"

# when the application is not running, start it with the the same --name value, if the executabable differs from this value, use the --cmd flag, for example
# firefox is searchable in pgrep with "firefox-bin" but the executable is "firefox"
wintoggle --name "firefox-bin" --cmd "firefox"

```

**Note** The application window will be focused to the monitor where the mouse is.

### Centering Window at Cursor

You can use the `--center-at-cursor` flag to display the window centered on the cursor position:

```bash
wintoggle --name "firefox" --center-at-cursor
```

### Hooks

If you'd like to execute some scripts or commands during activate and minimize events, you can use the `--on-activate` and `--on-minimize` flags. For example, if you wanted
to play some sounds during these events, here's how you could go about it:

```bash
wintoggle --name "firefox" --on-activate "ffplay -nodisp -autoexit $HOME/sounds/activate.mp3" --on-minimize "ffplay -nodisp -autoexit $HOME/sounds/minimize.mp3"
```

### Unmapping Windows

You can use the `--unmap` flag to remove the window from the window list when hiding (instead of just minimizing):

```bash
wintoggle --name "firefox" --unmap
```

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
