---
title: "Terminal and dpkg errors"
date: 2006-09-26
forum: Desktop Environments
---

### Post by lwr on 2006-09-26
Everytime I start the terminal, I get this error message:
```
bash: /bin/uname: Permission denied
bash: /bin/uname: Permission denied
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected

```
I also get errors whenever I try and install something, eg:
```
bash: /bin/tar: Permission denied

```
I've been doing so much to my system today that I can't pinpoint what's caused it, but any help you can offer would be very much appreciated.
Thanks

---

### Post by LotsOfPhil on 2006-09-26
What do you get when you type:

```
cat ~/.bashrc
```

---

### Post by lwr on 2006-09-26
Here's what I get:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

Thanks for your help.

---

### Post by LotsOfPhil on 2006-09-26
Hmm. I am pretty close to stumped. Do you have any other user accounts you could try using? If not, maybe set up a new one and see if they have the same problems.

---

