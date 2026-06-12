---
title: "[SOLVED] Cube doesn't work!"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by bioShark on 2007-07-03
Hi All

I have recently installed Ubuntu 7.04. Yesterday, when I finally installed my graphics card, I have checked the desktop effects, especially the cube roll over. I'm guessing that by doing that I have activated Compiz.
Well I have made some small installations like: codecs, skype, vlc. Now, the cube, doesn't roll. I am not sure what I did, but I'm guessing I have somehow deactivated it, because I also had only 1 workspace (instead of 2 or 4). I have solved this by going to the properties of the workspace.

Does anybody know where the options for activate/deactivate the cube are? Or what I should do?

Thanks in advance!

c.u.

---

### Post by sailor2001 on 2007-07-03
I never had much luck with the desktop effects..... download beryl and beryl manager from synaptics......then the fun begins

---

### Post by tutua on 2007-07-03
aha, new feisty means you must have a fresh .basrc? could you poss post it up here as I deleted mine by accident...?
The cube/desktop effects are simply in menu->system->Desktop Effects

---

### Post by Alex&amp;Linux on 2007-07-03
I agree with Sailor
Beryl is much better, and you may customize it to any level of complexity.
Fun indeed, and you can actually be more productive with the functionality the manager brings!

---

### Post by bioShark on 2007-07-03
Hi 

I didn't really wanted to work with the cube...I just wanted to see how it is and taste the feeling. That's why I didn't bother installing beryl. 

My PC is not the best one, so I am not sure if beryl will work correctly on it will slow my PC down:

PC: Intel Celeron 1300; 384 MB RAM; GeForce4 MX 440 with 128MB.

That's my junior PC.

---

### Post by pnix on 2007-07-03
```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```
run these two commands will roll your cube.

---

### Post by bioShark on 2007-07-03
tutua, here is the content of .bashrc:


# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

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

---

### Post by bodhi.zazen on 2007-07-03
Thread moved ;)

Neither Compiz nor Beryl are considered "beginners topics" if you will, and there are a lot of questions.

As both are popular and both are considered "beta" this forum was established.

---

### Post by bioShark on 2007-07-03
> **pnix said:**
> ```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```
run these two commands will roll your cube.

Thanks a lot.....it's working!


THE CUBE is ALIVEEEEE!!!!!

---

### Post by tutua on 2007-07-03
thanks rollandsov!!

---

