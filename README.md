# My personal Zsh setup with iTerm2

This repository shows the setup of my terminal and some other tools/aliases. All theme and scheme files are provided in an other [repository](https://github.com/se-jaeger/hunter-zsh-scheme), have a look!  


## Tool stack

- macOS
- [iTerm2](https://www.iterm2.com)
- [Zsh](http://zsh.org)
- [oh-my-zsh](http://ohmyz.sh)


### iTerm2

> **What is iTerm2?**  
> iTerm2 is a replacement for Terminal and the successor to iTerm. It works on Macs with macOS 10.10 or newer. iTerm2 brings the terminal into the modern age with features you never knew you always wanted.
>> (Source: https://www.iterm2.com)

I extensively use the `Split Panes`, `Mouseless Copy` and of course the `256 Colors` + `Configurability`. There are lot more for example the `Inline Images`. Take a [look](http://iterm2.com/features.html).


### Zsh

Zsh is like a superset of the standard `BASH`. It adds the following advantages:
- better autocompletion (case insensitive..)
- path expansion (cd /v/w [tab] == cd /var/www)
- syntax highlighting
- spelling correction
- ... much more useful pllugins
- oh-my-zsh


### oh-my-zsh

> Oh My Zsh is an open source, community-driven framework for managing your zsh configuration.
>> (Source: https://github.com/robbyrussell/oh-my-zsh)

It also comes with a lot of `themes` and `plugins`.



## 1. Install required tools

To activate changes you can restart iTerm2, if you did some changes on them, or reload the zsh config file: `source ~/.zshrc`


### Zsh

The easiest way to install Zsh is using [brew](https://brew.sh).  
Therefore run: `brew install zsh`


### oh-my-zsh

As you can see on: http://ohmyz.sh - use the following command to install oh-my-zsh.  
`sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`


### iTerm2

Download and install iTerm2. [Click](https://www.iterm2.com/downloads.html)  
Or use brew: `brew cask install iterm2`


## 2. Setup iTerm2


### Change iTerm2 colors

I changed colors of iTerm2 and provide the changes in an `itermcolors` file.

1. Download the `itermcolors` file. You can use the following command to automatically store it in your `oh-my-zsh` installation path, subdir `custom`, or use a custom one.
    - `curl https://raw.githubusercontent.com/se-jaeger/hunter-zsh-scheme/master/hunter.itermcolors > ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/hunter.itermcolors`
    - https://github.com/se-jaeger/hunter-zsh-scheme/blob/master/hunter.itermcolors
2. Import `hunter.itermcolors` (or whatever you named it) into iTerm2
    - iTerm2 -> Preferences -> tab "Profiles" -> select <your-profile-name> -> tab "Colors" -> Color Presets... -> Import... -> choose the `hunter.itermcolors` file
3. Select the scheme `hunter` (or whatever you named it)
    - iTerm2 -> Preferences -> tab "Profiles" -> select <your-profile-name> -> tab "Colors" -> Color Presets... -> `hunter`


### Enable word jumps and delete wohle words in iTerm2

- iTerm2 -> Preferences -> tab "Profiles" -> select <your-profile-name> -> tab "Keys" -> Load Presets... -> select "Natural Text Editing"

(Source: https://apple.stackexchange.com/a/293988)


### Change iTerm2 scheme

- iTerm2 -> Preferences -> tab "Appearance" -> Theme -> slect "Dark"

### Increase scroll buffer

- iTerm2 -> Preferences -> tab "Terminal" -> tick "Unlimited scrollback"


## 3. Install zsh plugins

### Install zsh plugin: zsh-autosuggestions

> It suggests commands as you type, based on command history.
>> (Source: https://github.com/zsh-users/zsh-autosuggestions#zsh-autosuggestions)

1. Run `git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`
2. Change your `~/.zshrc` file and add `zsh-autosuggestions` to the plugins like:
```
plugins(
  # other plugins
  zsh-autosuggestions
)
```
(Source: https://github.com/zsh-users/zsh-autosuggestions#oh-my-zsh)


### Install zsh plugin: zsh-syntax-highlighting

> It enables highlighing of commands whilst they are typed at a zsh prompt into an interactive terminal. This helps in reviewing commands before running them, particularly in catching syntax errors.
>> (Source: https://github.com/zsh-users/zsh-syntax-highlighting#zsh-syntax-highlighting-)

1. Run `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`
2. Change your `~/.zshrc` file and add `zsh-syntax-highlighting` to the the plugins like:
```
plugins(
  # other plugins
  zsh-syntax-highlighting
)
```
(Source: https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md#oh-my-zsh)

### Install zsh plugin: zsh-completions

> This projects aims at gathering/developing new completion scripts that are not available in Zsh yet. The scripts may be contributed to the Zsh project when stable enough.
>> (Source: https://github.com/zsh-users/zsh-completions)

1. Run `git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-completions`
2. Change your `~/.zshrc` file and add `zsh-completions` to the the plugins like:
```
plugins(
  # other plugins
  zsh-completions
)
```
3. Add `autoload -U compinit && compinit -i` to your `~/.zshrc` file. **BE CAREFUL: `-i` skips the security check!**
(Source: https://github.com/zsh-users/zsh-completions#using-zsh-frameworks)


### Install zsh plugin: zsh-history-substring-search

> This is a clean-room implementation of the Fish shell's history search feature, where you can type in any part of any command from history and then press chosen keys, such as the UP and DOWN arrows, to cycle through matches.
>> (Source: https://github.com/zsh-users/zsh-history-substring-search#zsh-history-substring-search)

1. Run `git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search`
2. Change your `~/.zshrc` file and add `zsh-history-substring-search` at the end of the plugins like. Just to make sure it is loaded after `zsh-syntax-highlighting`:
```
plugins(
  # other plugins

  # should be last plugin loaded
  history-substring-search
)
```
(Source: https://github.com/zsh-users/zsh-history-substring-search#install)


## 4. Setup oh-my-zsh theme

I created a `zsh-theme` file, which provide different features and change appearance, see [Click](https://github.com/se-jaeger/hunter-zsh-scheme).

1. Download the `zsh-theme` file. You can use the following command to automatically store it in the `themes` dir of your installation directory, or download it yourself.
    - `curl https://raw.githubusercontent.com/se-jaeger/hunter-zsh-scheme/master/hunter.zsh-theme > ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/hunter.zsh-theme`
    - https://github.com/se-jaeger/hunter-zsh-scheme/blob/master/hunter.zsh-theme
2. Activate the theme in `~/.zshrc` file: `ZSH_THEME="hunter"` (or whatever you named it)


# Screenshots

![Showing features](https://raw.githubusercontent.com/se-jaeger/my-zsh/master/screenshots/hunter_screenshot.png)

# Further tooling

## useful command line tools

A collection of different tools I'm using.


### trash

Moves file and folders to Trash, like the `Move to Trash` option in context menu.  
Easy install via brew: `brew install trash`


### tree 

> Tree is a recursive directory listing command that produces a depth indented listing of files.
>> (Source: http://mama.indstate.edu/users/ice/tree/) 

Easy install via brew: `brew install tree`


### tldr

> Simplified and community-driven man pages.
>> (Source: http://tldr.sh)

Easy install via brew: `brew install tldr`


## useful alias

A collection of different alias I'm using.

- `alias del="trash"` -> just add it to your `~/.zshrc`
- a lot of aliases which are provided by oh-my-zsh
    - `gst='git status'`
    - `ga='git add'`
    - `gaa='git add --all'`
    - `gcmsg='git commit -m'`
    - `gp='git push'`
    - for a list of all aliases type `alias`

