---
title: "Can't start any game from Menu"
date: 2018-02-18
forum: Desktop Environments
---

### Post by stii on 2018-02-18
If i try clicking on anything that is under **Games** section in menu, I get the message *Invalid desktop entry file: '/usr/share/applications/<game>.desktop'*. But I don't understand why, .desktop files look alright to me.

Here is the desktop file for pysolfc:

```
[Desktop Entry]
Name=PySol Fan Club Edition
Exec=pysolfc
Terminal=false
Type=Application
Categories=Game;CardGame;
Keywords=Game;CardGame;
Icon=/usr/share/icons/pysol01.png
```

And when I click on pysol in Menu, I get the message [I]Invalid desktop entry file: '/usr/share/applications/pysol.desktop'.
[/I]
I do have _/usr/games_ in **$PATH**:
```
$ printenv PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:/usr/games
```

I can run games from the terminal,  but not from the Run window which can't even find games.

---

### Post by vasa1 on 2018-02-18
Can you install *gnome-sudoku* and see if that appears in your menu and works from there?

---

### Post by stii on 2018-02-18
> **vasa1 said:**
> Can you install *gnome-sudoku* and see if that appears in your menu and works from there?

```
Invalid desktop entry file: '/usr/share/applications/gnome-sudoku.desktop'
```

---

### Post by vasa1 on 2018-02-18
Is yours a full Lubuntu install and of which version?

Does *sudo apt-get update* followed by *sudo apt-get dist-upgrade* show any errors?

---

### Post by stii on 2018-02-18
> **vasa1 said:**
> Is yours a full Lubuntu install and of which version?

Does *sudo apt-get update* followed by *sudo apt-get dist-upgrade* show any errors?

Yes, full 32-bit version from the official Lubuntu website. Version of Ubuntu release is 17.10 (before that I had 17.04, but the issue was present then too).

No, *sudo apt-get update && sudo apt-get dist-upgrade* work fine.

---

### Post by stii on 2018-03-06
If I execute ```
lxpanelctl exit
``` And then I execute ```
lxpanel&
``` New default menu (the one you get when you install Lubuntu) will spawn. I can run games from the menu of this panel without problems.

What does this mean?

---

### Post by stii on 2018-03-06
Hmmm... if I issue
```
lxpanelctl exit
```
and after that
```
lxpanel --profile LXDE
```
I can run games. So it's not a config file.

I alsto tried making lxpanel execute last in ~/.config/lxsession/LXDE/autostart, but it did not help.

Executing ```
lxpanelctl restart
``` has no effect (it does what it's supposed to, it just doesn't "fix" my issue).

---

### Post by stii on 2018-03-06
I think I now know what is the root of the problem, just don't know how to fix it.

I  commented the line that adds Games to the $PATH. Then I logged out, logged  back in and tried stopping the panel and starting it again. But this time, new  panel displayed the same error when I tried to launch the game.

Because of that I think that the problem is that *~/.config/lxsession/LXDE/autostart* is read before *~/.bashrc*  which adds Games to the path. Therefore, the panel that is started by  the autostart script doesn't know how to find games, but the one that is  started after knows.

If someone of you knows how to make to .bashrc is read before autostart, please write how here.

---

### Post by stii on 2018-03-06
I also tried starting, stopping and starting again lxpanel in autostart script (with uncommented line that adds Games to the $PATH in .bashrc), and I couldn't run games from the Menu. This confirms my suspicion (explained in the post above).

Then I removed the lines that stop and start (for the second time) lxpanel and added at the top of the autostart script ```
@/bin/sh source /home/$USER/.bashrc
``` which (strangely) didn't do anything.

---

### Post by stii on 2018-03-06
I just put ```
export PATH=$PATH:/usr/games
``` at the top of the .bashrc and it solved my problem.
I don't understand why this solved my problem, so if someone knows please tell me.

Here is my (barely changed) .bashrc:

```
export PATH=$PATH:/usr/games
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=
HISTFILESIZE=

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```

---

