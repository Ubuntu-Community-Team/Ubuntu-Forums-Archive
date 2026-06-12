---
title: "/home/.profile"
date: 2007-05-16
forum: Desktop Environments
---

### Post by hollowhead on 2007-05-16
I need some help in that I need to create a /home/.profile file to get some software that requires it to run.  What is this file and I assume copying across etc/profile will not work if not how do I go about creating one?

Ta in advance Hollowhead.

---

### Post by llamakc on 2007-05-16
You probably mean /home/YOURUSERNAME/.profile

and if so, you can just create the file in your home directory. As to the contents of the file, that would depend on WHAT software you are trying to get running. Give us more details.

---

### Post by hollowhead on 2007-05-16
llamakc, thanks for your relpy and you are right about the path.  I'm trying to run Qtiplot, the latest version,  I tried creating a .profile  in my home dir and adding this line to it (w/o the quotes)

"export QTDIR=/usr/local/Trolltech/Qt-4.2.3"

 which is what I am told I need to do to stop this error


/usr/bin/qtiplot
/usr/bin/qtiplot: symbol lookup error: /usr/bin/qtiplot: undefined symbol: _ZN12QApplicationC1ERiPPci

when I run the binary by its lead author.

However it didn't work assume I don't need the quotes?

Ta. Hollowhead.

---

### Post by taurus on 2007-05-16
Try adding that line, export QTDIR=/usr/local/Trolltech/Qt-4.2.3, to your ~/.bashrc.

```
gedit ~/.bashrc
```
Then, log out and back in again or reharsh it with

```
source ~/.bashrc
```

---

### Post by hollowhead on 2007-05-16
Cheers I will try it and post what happens.  Not very optimistic but you never know......

---

### Post by hollowhead on 2007-05-17
Tired adding the line to my bashrc as shown below don't really know what I am doing.

I've found some examples of profile files on the web I will try to build one although any advice would be welcome....


# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

export QTDIR=/usr/local/Trolltech/Qt-4.2.3

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

---

### Post by llamakc on 2007-05-17
You use BASH, so you need to add that line to your .bashrc, after doing so you need to either logout/login or from the terminal type:

source ~/.bashrc

Now, any changes made to the .bashrc file will apply.

---

### Post by hollowhead on 2007-05-17
llamakc, thanks for your reply, added it its the 4th line down.  I don't think the problem is anything to do with this anyway but before I email Ion again I was going to try creating a .profile file.  Neil.

---

### Post by llamakc on 2007-05-17
Does the directory path you're trying to export exist yet?

Also, certain dot files are used by certain shells.


sh      .profile  
csh	.cshrc
tcsh	.tcshrc or .cshrc
ksh	.profile
bash	.bash_profile, .bash_login or .profile

As your login shell is BASH, you would use any of those three, but be sure that your .bashrc is invoking them also.

---

### Post by hollowhead on 2007-05-17
Yes I installed Qt-4.2.3 without incident and like it, I might write an app if I can work out how to link qdesigner to c code.....

  My original error on running qtiplot was a complaint about not finding libQTassistant.so.4.  I set up symobolic links to all the files with  libQTassistant in their name in the Qt-4.2.3/lib folder to usr/lib.  Then the error changed to the one above.  I have been downloading debs of qtiplot and using it happliy until Ion switched QT libs.  I will attempt to create a .profile file but I now don't think this is the problem.  I think Ion has comilied against a slightly different version of the QT lib. 

Ta.  Neil

---

