---
title: ".dmrc error - and setting paths - and making things occur at startup Q"
date: 2005-10-30
forum: Desktop Environments
---

### Post by jacknel on 2005-10-30
1.
OK trying to put all my Q  into one thing so i don't cause clutter

.dmrc permissions error - now  i know this has been posted a couple times but i have gone through to no avail....

here's the thing, it says permissions of file needs to be owened by owner (it is Justin and group is ADM), and be 644 which it is.

i know there is the work around about relaxing permissions and such, but was wandering if there is anyway to FIX it.

2.
Can someone tell me how to set paths at the beginning?

i am trying to add this

NR_INCLUDE_PATH=/usr/genarts/sapphire-nreal/include; export NR_INCLUDE_PATH
NR_ICON_PATH=/usr/genarts/sapphire-nreal/icons; export NR_ICON_PATH

if i type it in terminal it only stays resident for the time terminal is open and i have to run things from that terminal...

I have read instructions and placed it in the /etc/profile 

> 
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

export PATH

  NR_INCLUDE_PATH=/usr/genarts/sapphire-nreal/include; export NR_INCLUDE_PATH
  NR_ICON_PATH=/usr/genarts/sapphire-nreal/icons; export NR_ICON_PATH

umask 022


and have also tried putting it in the users .bash_profile 

> 
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

PATH=$PATH:$HOME/bin:/usr/nreal/bin:
NR_INCLUDE_PATH=/usr/genarts/sapphire-nreal/include
NR_ICON_PATH=/usr/genarts/sapphire-nreal/icons
export NR_INCLUDE_PATH
export NR_ICON_PATH
export PATH



3. LAST of all...

I have a DVB tuner and every time i restart my pc i have to enter the following command

modprobe -v dvb-bt8xx

anyway to make this auto?

THX heaps for any help

---

### Post by jacknel on 2005-11-01
bump?

---

