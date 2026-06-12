---
title: "Problem with terminal"
date: 2012-09-22
forum: Desktop Environments
---

### Post by h66m9d on 2012-09-22
hi:)
when I open "terminal" and going to bash, then I close that it warn me:
> There is still a process running in this terminal. Closing the terminal will kill it.
I haven't any open software in terminal but show that.

---

### Post by Lars Noodén on 2012-09-22
Did you type anything in the terminal?  If so, what?  Also, which version of Ubuntu are you using?

---

### Post by matt_symes on 2012-09-22
Hi

Can you post the output of

```
cat ~/.bashrc
```That is where is would look as well.

Kind regards

---

### Post by spier on 2012-09-22
When you open a terminal, automatically you start a bash session!

If you then type 
```
$ bash
``` you'll open another session within the first one!

Thus, the complain when you close the terminal window without exiting the inner session...

---

### Post by h66m9d on 2012-09-22
> **Lars Noodén said:**
> Did you type anything in the terminal?  If so, what?  Also, which version of Ubuntu are you using?
I use ubuntu 12.4 and i type below text in terminal:
> hamed@hamed-desktop:~$ sudo bash
[sudo] password for hamed:
root@hamed-desktop:~#

[img]http://www.imagetoo.com/images/screengng.png[/img]

---

### Post by h66m9d on 2012-09-22
> **matt_symes said:**
> Hi

Can you post the output of

```
cat ~/.bashrc
```That is where is would look as well.

Kind regards

That result is:
```

root@hamed-desktop:~# cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
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
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

---

### Post by Lars Noodén on 2012-09-22
> **h66m9d said:**
> I use ubuntu 12.4 and i type below text in terminal:
<snip>

There you have it.  You have a second instance of bash running as root.  You'll have to exit root's bash first to avoid that message.  Bash can be exited by pressing ctrl-D or entering [font=Courier New]exit[/font]

---

### Post by h66m9d on 2012-09-22
> **Lars Noodén said:**
> There you have it.  You have a second instance of bash running as root.  You'll have to exit root's bash first to avoid that message.  Bash can be exited by pressing ctrl-D or entering [font=Courier New]exit[/font]

yes. now I understand:lolflag:
Thanks friends ;)

---

### Post by RichTheCoder on 2013-03-17
I just installed sqlite from source on my Ubuntu 11.10 box. I never typed "bash" or any other shell's name during the session, but, apparently the "make" or the sqlite3 program shelled out a few times and did not exit. (I did misuse sqlite3 a good bit.) After four CTRL-D presses with this response: 
an echo of    exit    and another prompt, 
the 5th try closed my terminal window.

---

