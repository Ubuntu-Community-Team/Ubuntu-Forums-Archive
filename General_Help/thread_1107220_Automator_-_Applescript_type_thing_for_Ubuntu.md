---
title: "Automator - Applescript type thing for Ubuntu"
date: 2009-03-26
forum: General Help
---

### Post by caavoom on 2009-03-26
Please help. I find myself doing repetitive task everyday like backing up my laptop files to my external hdd using Rsync, running sudo apt-get autoremove, autoclean, clean after a system update, emptying the trash, amongst other things. 

I was wondering if there is an workflow creator that somehow works the same way as Automator in Mac OS X. 

Thanks

---

### Post by absolutezero1287 on 2009-03-26
I don't know about automator but it sounds like your problems can be solved by writing a simple script or scripts. What specifically do you wish to automate?

Example:
```

#!/bin/bash
gnome-terminal -e "sudo apt-get update"

```

Place that in /etc/cron.daily/ so that it updates the system every day or cron.weekly.

One a side note: If you want to make commands shorter add aliases in your .bashrc.

Here's mine:
```

if [[ $- != *i* ]] ; then
	# Shell is non-interactive.  Be done now!
	return
fi

#-------------------------------------------------------------
# Shell Prompt
#-------------------------------------------------------------

# Set colorful PS1 only on colorful terminals.
# dircolors --print-database uses its own built-in database
# instead of using /etc/DIR_COLORS.  Try to use the external file
# first to take advantage of user additions.  Use internal bash
# globbing instead of external grep binary.
safe_term=${TERM//[^[:alnum:]]/?}   # sanitize TERM
match_lhs=""
[[ -f ~/.dir_colors   ]] && match_lhs="${match_lhs}$(<~/.dir_colors)"
[[ -f /etc/DIR_COLORS ]] && match_lhs="${match_lhs}$(</etc/DIR_COLORS)"
[[ -z ${match_lhs}    ]] \
	&& type -P dircolors >/dev/null \
	&& match_lhs=$(dircolors --print-database)
[[ $'\n'${match_lhs} == *$'\n'"TERM "${safe_term}* ]] && use_color=true

if ${use_color} ; then
	# Enable colors for ls, etc.  Prefer ~/.dir_colors #64489
	if type -P dircolors >/dev/null ; then
		if [[ -f ~/.dir_colors ]] ; then
			eval $(dircolors -b ~/.dir_colors)
		elif [[ -f /etc/DIR_COLORS ]] ; then
			eval $(dircolors -b /etc/DIR_COLORS)
		fi
	fi

	if [[ ${EUID} == 0 ]] ; then
		PS1='\[\033[01;31m\]\h\[\033[01;34m\]\W\$\[\033[00m\]>'
	else
		PS1='\[\033[01;32m\]\u@\h\[\033[01;34m\]\w\$\[\033[00m\]>'
	fi

	alias ls='ls --color=auto'
	alias grep='grep --colour=auto'
else
	if [[ ${EUID} == 0 ]] ; then
		# show root@ when we don't have colors
		PS1='\u@\h\W\$>'
	else
		PS1='\u@\h\w\$>'
	fi
fi

unset use_color safe_term match_lhs
#-------------------------------------------------------------
# Term title
#-------------------------------------------------------------
case ${TERM} in
	xterm*|rxvt*|Eterm|aterm|kterm|gnome*|interix|terminal*|xfce*)
		PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME%%.*}:${PWD/$HOME/~}\007"'
		;;
	screen)
		PROMPT_COMMAND='echo -ne "\033_${USER}@${HOSTNAME%%.*}:${PWD/$HOME/~}\033\\"'
		;;
esac

use_color=false

#-------------------------------------------------------------
# Automatic setting of $DISPLAY (if not set already).
# This works for linux - your mileage may vary. ... 
# The problem is that different types of terminals give
# different answers to 'who am i' (rxvt in particular can be
# troublesome).
# I have not found a 'universal' method yet.
#-------------------------------------------------------------

function get_xserver ()
{
    case $TERM in
       xterm*|rxvt*|Eterm|aterm|kterm|gnome*|interix|terminal*|xfce*)
            XSERVER=$(who am i | awk '{print $NF}' | tr -d ')''(' ) 
            # Ane-Pieter Wieringa suggests the following alternative:
            # I_AM=$(who am i)
            # SERVER=${I_AM#*(}
            # SERVER=${SERVER%*)}

            XSERVER=${XSERVER%%:*}
            ;;
    esac  
}

if [ -z ${DISPLAY:=""} ]; then
    get_xserver
    if [[ -z ${XSERVER}  || ${XSERVER} == $(hostname) || \
      ${XSERVER} == "unix" ]]; then 
        DISPLAY=":0.0"          # Display on local host.
    else
        DISPLAY=${XSERVER}:0.0  # Display on remote host.
    fi
fi

export DISPLAY


#--------------------------------------------------------------
#Aliases
#--------------------------------------------------------------
#
#
# here are a few for apt
alias "apt-get"="sudo apt-get"
alias "apt-key"="sudo apt-key"
alias "apt-cd"="sudo apt-cdrom"
alias "apt-toss"="sudo apt-get --purge remove"
alias "apt-find"="sudo apt-cache search"
#
#
# some for commonly used apps
alias nautilusr="sudo nautilus"
alias geditr="sudo gedit"
alias vimr="sudo vim"
alias visudo="sudo visudo"
alias gparted="sudo gparted"
alias synaptic="sudo synaptic"
##alias keyadd="sudo "
#might get around to it...
alias killall="sudo killall"
#--------------------------------------------------------------
#Misc
#--------------------------------------------------------------
export PATH="$PATH:/home/chowder/bin"
#adds ~/bin to $PATH

```

Hope this helps in some way or another.

---

### Post by caavoom on 2009-03-26
Thanks for the quick reply. What i have in mind is something like a script that includes multiple commands (sudo or not) (like my rsync commands, autoremove, autoclean, etc) and have a button or an icon that I can place in the panel which I can click and it will do all the task in one go.

---

### Post by absolutezero1287 on 2009-03-26
> **caavoom said:**
> Thanks for the quick reply. What i have in mind is something like a script that includes multiple commands (sudo or not) (like my rsync commands, autoremove, autoclean, etc) and have a button or an icon that I can place in the panel which I can click and it will do all the task in one go.

That's doable. You would need to write the script, make it executable, and store it somewhere you won't forget. I suggest making a ~/bin directory and adding it to $PATH just like I did at the bottom of my .bashrc which also goes in the home directory.

Doing this any script you write in ~/bin will be read without having to write out the full directory.

```

mdkir ~/bin
cd ~
gedit .bashrc
#add whatever you want
source .bashrc
#reads the changes and applies them
cd ~/bin
gedit foo
#save it!
foo
#this should execute your program

```

If you're using gnome then you can make a custom launcher to launch your script. Lets revisit the idea of an update script.

```

#!/bin/bash
gksudo apt-get update
#we use gksudo here so that there is no
#need to open up a terminal

```

What you should now about BASH is that it is a powerful shell scripting language and can be used for greater things than automation of menial tasks. If you took the time to learn AppleScript then its worth a shot to look at a few bash tutorials online.

---

### Post by ajgreeny on 2009-03-26
You should be able to do it all with a script like this:-
```
#!/bin/bash
command 1
command 2
command 3
```
The only possible problem is any of the commands that require your password to be entered, which will not work unless you make the actions executable without the password being entered.  I know there is a way to do that but I'm not sure how, so wait for more answers..

---

### Post by absolutezero1287 on 2009-03-26
> **ajgreeny said:**
> You should be able to do it all with a script like this:-
```
#!/bin/bash
command 1
command 2
command 3
```
The only possible problem is any of the commands that require your password to be entered, which will not work unless you make the actions executable without the password being entered.  I know there is a way to do that but I'm not sure how, so wait for more answers..

You can solve the password problem  by putting gksu(do) in front of the command or modifying the sudoers file to allow the user to execute a certain command without the need for root permissions. The former method is far easier and modifying the sudoers file poses security risks.

---

### Post by ajgreeny on 2009-03-26
> **absolutezero1287 said:**
> You can solve the password problem  by putting gksu(do) in front of the command or modifying the sudoers file to allow the user to execute a certain command without the need for root permissions. The former method is far easier and modifying the sudoers file poses security risks.
Thanks for that, I will make a note of that method for future reference, as it could be extremely useful.
Every day I learn a little bit more about this wonderful OS!

---

### Post by caavoom on 2009-03-26
Thanks for replies. I'll definetely give it a shot.

---

