# Dotfiles

This repository contains my dotfiles, managed with [Chezmoi](https://www.chezmoi.io/).

## Setup

To retrieve the age key needed for encrypted files:

```bash
bw get item "age-key" | jq -r '.notes' > ~/.config/age/keys.txt
```

Create the chezmoi configuration file at `~/.config/chezmoi/chezmoi.toml` with the following content:

```toml
encryption = "age"
[age]
    identity = "/home/scott/.config/age/keys.txt"
    recipient = "age18d505mal4qfe6r8ykxu4e4pggv4m3ny5fxztm25ge659pg3eks6s2ry2uj"
```

After setting up the age key and configuration, you can apply the dotfiles with:

```bash
chezmoi apply
```