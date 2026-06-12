---
title: "Colourful terminals anyone?"
date: 2009-06-12
forum: General Help
---

### Post by uberlube on 2009-06-12
I just gave Sabayon a spin to see what was new and found myself only halfway impressed. One thing that did catch my eye though was how colourful the the terminal was. I wouldnt mind seeing that in my setup. Any suggestions as to a download?

---

### Post by robobart on 2009-06-12
Have you checked out this?

[http://ubuntuforums.org/showthread.php?t=470626](http://ubuntuforums.org/showthread.php?t=470626)

Or do you want even more color....

---

### Post by maheshasolkar on 2009-06-12
Is there a screenshot to see what you mean?

---

### Post by maheshasolkar on 2009-06-12
As far as prompt goes, here are a few references I use:

  [http://www.nparikh.org/unix/prompt.php](http://www.nparikh.org/unix/prompt.php) (tcsh/zcsh)
  [http://wiki.archlinux.org/index.php/Color_Bash_Prompt](http://wiki.archlinux.org/index.php/Color_Bash_Prompt)

I also set the following alias to make directory listing colorful:

  alias ls 'ls --color'

---

### Post by uberlube on 2009-06-12
ive been trying to find one, ill get back to u in a sec

---

### Post by benj1 on 2009-06-12
you want a program call dircolors. its already installed in ubuntu, it allows you to define colours for file types in ls etc, if youre into python try ipython, that has built in syntax highlighting, thats very colourful.

---

### Post by uberlube on 2009-06-12
wow now THIS is what im talking about! make a .bashrc for your home folder and add this into it, you wont be dissapointed :p

```
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

# Colors

Black="$(tput setaf 0)"
BlackBG="$(tput setab 0)"
DarkGrey="$(tput bold ; tput setaf 0)"
LightGrey="$(tput setaf 7)"
LightGreyBG="$(tput setab 7)"
White="$(tput bold ; tput setaf 7)"
Red="$(tput setaf 1)"
RedBG="$(tput setab 1)"
LightRed="$(tput bold ; tput setaf 1)"
Green="$(tput setaf 2)"
GreenBG="$(tput setab 2)"
LightGreen="$(tput bold ; tput setaf 2)"
Brown="$(tput setaf 3)"
BrownBG="$(tput setab 3)"
Yellow="$(tput bold ; tput setaf 3)"
Blue="$(tput setaf 4)"
BlueBG="$(tput setab 4)"
LightBlue="$(tput bold ; tput setaf 4)"
Purple="$(tput setaf 5)"
PurpleBG="$(tput setab 5)"
Pink="$(tput bold ; tput setaf 5)"
Cyan="$(tput setaf 6)"
CyanBG="$(tput setab 6)"
LightCyan="$(tput bold ; tput setaf 6)"
NC="$(tput sgr0)"       # No Color

# Functions

spin ()
{
echo -ne "$White-"
echo -ne "$LightGray\b|"
echo -ne "$LightGreen\bx"
sleep .02
echo -ne "$LightBlue\b+$RC"
}

typetext1 ()
{
sleep .02
echo -ne "$LightGreen W"
sleep .02
echo -ne e
sleep .02
echo -ne l
sleep .02
echo -ne c
sleep .02
echo -ne o
sleep .02
echo -ne m
sleep .02
echo -ne e
sleep .02
echo -ne " "
sleep .02
echo -ne t
sleep .02
echo -ne o
sleep .02
echo -ne " "
sleep .02
echo -ne "$HOSTNAME $NC"
sleep .02
}

typetext2 ()
{
sleep .02
echo -ne "$LightGreen E"
sleep .02
echo -ne n
sleep .02
echo -ne j
sleep .02
echo -ne o
sleep .02
echo -ne y
sleep .02
echo -ne " "
sleep .02
echo -ne y
sleep .02
echo -ne o
sleep .02
echo -ne u
sleep .02
echo -ne r
sleep .02
echo -ne " "
sleep .02
echo -ne s
sleep .02
echo -ne t
sleep .02
echo -ne a
sleep .02
echo -ne y
sleep .02
echo -ne "! "
sleep .02
}

dots ()
{
sleep .5
echo -ne "$LightGreen ."
sleep .5
echo -ne .
sleep .5
echo -ne .
sleep .8
echo -ne "$LightBlue done"
}

#Distribution
DISTRO="Unknown Distro"
DISTRO='Ubuntu 8.04 "Hardy Heron"'

memfree="`cat /proc/meminfo | grep MemFree | cut -d: -f2 | cut -dk -f1`";
memtotal="`cat /proc/meminfo | grep MemTotal | cut -d: -f2 | cut -dk -f1`";
memfreepcnt=$(echo "scale=5; $memfree/$memtotal*100" | bc -l);

# Welcome screen

clear;
echo -e "";
for i in `seq 1 15` ; do spin; done; typetext1; for i in `seq 1 15` ; do spin; done ;echo "";
echo "";
echo -ne "$LightBlue Hello $LightGreen$USER $LightBlue!";
echo ""; sleep .3;
echo "";
echo -ne "$LightBlue Today is: $LightGreen`date`";
echo ""; sleep .3;
echo -ne "$LightBlue Last login:$LightGreen `lastlog | grep $USER | awk '{print $4" "$6" "$5" "$9}'`$LightBlue at$LightGreen `lastlog | grep $USER | awk '{print $7}'`$LightBlue from$LightGreen `lastlog | grep $USER | awk '{print $3}'`";
echo ""; sleep .3;
echo "";
echo -ne "$LightBlue Loading system information"; dots; 
echo ""; sleep .3;
echo "";
echo -ne "$LightBlue Distro: $LightGreen $DISTRO";
echo "";
echo -ne "$LightBlue Kernel: $LightGreen `uname -smr`";
echo "";
echo -ne "$LightBlue CPU:   $LightGreen `grep "model name" /proc/cpuinfo | cut -d : -f2`";
echo "";
echo -ne "$LightBlue Speed:  $LightGreen`grep "cpu MHz" /proc/cpuinfo | cut -d : -f2` MHz"; 
echo "";
echo -ne "$LightBlue Load:   $LightGreen `w | grep up | awk '{print $10" "$11" "$12}'`";
echo "";
echo -ne "$LightBlue RAM:    $LightGreen `cat /proc/meminfo | head -n 1 | awk '/[0-9]/ {print $2}'` KB";
echo "";
echo -ne "$LightBlue Usage:  $LightGreen $memfreepcnt %"
echo "";
echo -ne "$LightBlue IP:     $LightGreen `/sbin/ip addr show ath0 | grep 'inet ' | cut -d t -f2 | cut -d / -f1 | cut -b 2-`";
echo "";
echo -ne "$LightBlue Uptime: $LightGreen `uptime | awk {'print $3" "$4" "$5'} | sed 's/:/ hours, /' | sed -r 's/,$/ minutes/'`";
echo ""; sleep .3;
echo "";
for i in `seq 1 21` ; do spin; done; typetext2; for i in `seq 1 20` ; do spin; done ;echo "";
echo "" $NC;

# Fancy bash

PS1='\[$LightBlue\]\[$LightGreen\]\u\[$LightBlue\]@\[$LightGreen\]\h\[$LightBlue\]:\[$LightGreen\]\w\[$LightBlue\]\$\[$NC\] '
```

---

### Post by maheshasolkar on 2009-06-12
Fancy indeed :)

However, personally I do prefer all that information in the Conky display. 

  [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

I'd much rather have terminal give me a prompt, well promptly, every time I start one to do little quick something.

---

