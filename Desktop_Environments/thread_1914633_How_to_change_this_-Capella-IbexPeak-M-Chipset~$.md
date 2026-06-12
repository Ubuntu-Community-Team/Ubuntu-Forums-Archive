---
title: "How to change this -Capella-IbexPeak-M-Chipset:~$  ?"
date: 2012-01-24
forum: Desktop Environments
---

### Post by hackum on 2012-01-24
Hello!

I desire change this of my terminal:


-Capella-IbexPeak-M-Chipset:~$ 


How to ?

Thanks you!

---

### Post by Krytarik on 2012-01-24
Open the file ".bashrc" in the home directory of your user, find these lines:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    **PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '**
    # PS1='${debian_chroot:+($debian_chroot)}[\u]:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    **PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"**
    # PS1="\[\e]0;${debian_chroot:+($debian_chroot)}[\u]: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```... and change them to your liking, with the help of the list of keys and their meanings you find here:

[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

The lines below the default ones are how I've set up my command prompt, thanks to your instigation, nice! :D

Notice that you need to re-open the Terminal for the changes to take effect, or at the tty, you need to relogin.

Regards.

EDIT: Just in case you want to change the computer name itself, not just the reflection of it in the command prompt; you'd need to change the concerning entries in both "/etc/hostname" and "/etc/hosts". (Just for the slight chance you eventually come back. ;-))

---

