---
title: "bashrc broke?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by passonno on 2006-07-04
Hello,

I have recently started having problems with my bash environment, when I open a terminal, I get the following:

    bash: alias: /home/anthony/Downloads/fst-1.7.1/fst: not found
bash: alias: VST/LoungeLizard.dll: not found
bash:
alias b4=sh: command not found
bash:

# enable programmable completion features (you dont: command not found
anthony@anthony-laptop:~$


I don't understand what I did wrong, but here is a copy of my .bashrc


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

#MY ALIASES
alias tascam='sudo fxload -s /home/anthony/Downloads/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/003/002
'
alias dss='dss.sh'
alias dsk='ls -al'
alias cls='clear'
#alias 3d='3ddesk --mode flip'
alias killname='killname.sh'
alias sdr='sdr.sh'
alias podget='podget.sh'
alias ubuntu='firefox http://www.ubuntuforums.org'
alias google='google.sh' 
alias kontakt='sh ~/Downloads/fst-1.7.1/fst VST/Kontakt2.dll &'
alias moog='sh ~/Downloads/fst-1.7.1/fst VST/MinimogueVA.dll &'
alias tron='sh ~/Downloads/fst-1.7.1/fst VST/Nanotron.dll &
alias rhodes='sh ~/Downloads/fst-1.7.1/fst VST/LoungeLizard.dll &'
alias b4='sh ~/Downloads/fst-1.7.1/fst ~/VST/b4 &'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi


Any clues as to what's wrong?

---

### Post by mlind on 2006-07-04
Have you set these yourself?
```

alias kontakt='sh ~/Downloads/fst-1.7.1/fst VST/Kontakt2.dll &'
alias moog='sh ~/Downloads/fst-1.7.1/fst VST/MinimogueVA.dll &'
alias tron='sh ~/Downloads/fst-1.7.1/fst VST/Nanotron.dll &
alias rhodes='sh ~/Downloads/fst-1.7.1/fst VST/LoungeLizard.dll &'
alias b4='sh ~/Downloads/fst-1.7.1/fst ~/VST/b4 &'

```

try using quotation (") marks instead. Looks like command is cut in two for
some reason

---

### Post by passonno on 2006-07-04
I did set them myself.  

So I should set them in "  instead of ' ?

I wonder why it broke though, because it worked fine with single quotes when I had one or two entries.

anyway,  thanks for the help, I'll check it myself in a moment.

---

### Post by passonno on 2006-07-04
Fixed it.

I guess the formatting was wrong at the end, but the other part was that the path was wrong in the last alias itself.

Anyway, I created a seperate .bash_aliases file, it's much cleaner.

thanks again.

---

