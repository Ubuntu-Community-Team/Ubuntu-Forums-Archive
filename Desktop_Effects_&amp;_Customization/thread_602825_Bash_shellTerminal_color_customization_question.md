---
title: "Bash shell/Terminal color customization question:"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by suchawato on 2007-11-04
Hello Folks:
So I don't have my linux book around to answer this question:
I tried to edit my terminal colors and prompt using the following sequence:
```
PS1="\e[0;40;1;33m[\d \t \u@\h \W]\$ "
```
Allowing date, time, and foreground set to yellow and background set to black.
However, this is not a permanent setting.
It will reset every time I open a new terminal.
I want to make it permanent.
Anybody?
I was thinking maybe my bash.bashrc file but I'm not sure.

---

### Post by bingoUV on 2007-11-04
add this line in your ~/.bashrc file
```

export PS1="\e[0;40;1;33m[\d \t \u@\h \W]\$ "

```

/etc/bash.bashrc will make this setting for all users.

---

### Post by suchawato on 2007-11-04
No, that didn't work.
I opened a new terminal, and it was white with standard.

---

### Post by suchawato on 2007-11-04
Thanks, but that didn't work.
I opened a new terminal, and it was white with standard.

---

### Post by suchawato on 2007-11-04
For some reason, I am unable to edit posts I've made at the moment.
I wonder if they turned that feature back on after doing the system maintenance earlier.

---

### Post by suchawato on 2007-11-05
Here is a copy of my bash.bashrc file:
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
                /usr/bin/python /usr/lib/command-not-found -- $1
                return $?
	}
fi
export PS1="\e[0;40;1;33m[\d \t \u@\h \W]\$ "
```

---

### Post by suchawato on 2007-11-05
This is a clue I think:
From the bash.bashrc file:
> # System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.
What does "file has to be sourced in /etc/profile." mean?

---

### Post by ayoli on 2007-11-05
try this in your ~/.bashrc
CYAN="\[\033[1;36m\]"
export PS1="\e[$CYAN\d \t \u@\h \W]\$ "

replace cyan with color you want

---

### Post by suchawato on 2007-11-05
What would I need to do to change both bacground and text?
And would this string add the date and time as well?

---

### Post by ayoli on 2007-11-05
> **suchawato said:**
> What would I need to do to change both bacground and text?
And would this string add the date and time as well?

Actually, for the background I don't know but the easiest way is to choose a color scheme in gnome-terminal (right clik , choose edit current profile).
For the time I use :
$(date \"+%H:%M\")
and for the date:
$(date \"+%a,%d %b %y\")
btw your string should add date and time like this:
day month daynum HH:MM:SS

---

### Post by totalnub on 2007-11-05
well, I just stumbled across this thread and was doing something similar yesterday :)

what i did was edit my .bashrc (~/.bashrc not the global one)
i just put 
PS1=my prompt settings"

and i commented out the existing one. I'll upload my file so you can see.

---

### Post by jovinbasil on 2007-12-17
Hi, I had selected the terminal to close after the command, no as soon as i open a terminal it vanishes. How do I change the settings to hold the terminal.

---

