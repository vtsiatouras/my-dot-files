# Dot files

This repo contains my configuration dotfiles of my Debian workstation. These are mostly terminal configs, such as zsh + tmux, some theming etc.

![image](https://user-images.githubusercontent.com/25209180/175320627-e3dee7bf-b420-49c6-bf17-38402edc9904.png)

### Installation instructions

```
git clone --bare git@github.com:vtsiatouras/my-dot-files.git $HOME/.cfg
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
config checkout
```

If `config checkout` fails run (this happens when there is an existing `.cfg/` directory on your `$HOME`):

```
mkdir -p .config-backup && \
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
xargs -I{} mv {} .config-backup/{}
```

Then execute again:

```
config checkout
```

Final step:

```
config config --local status.showUntrackedFiles no
```

### Example usage

```
config status
config add .vimrc
config commit -m "Add vimrc"
config add .bashrc
config commit -m "Add bashrc"
config push
```

