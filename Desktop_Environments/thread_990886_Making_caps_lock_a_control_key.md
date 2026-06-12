---
title: "Making caps lock a control key"
date: 2008-11-23
forum: Desktop Environments
---

### Post by Leo Simon on 2008-11-23
A widely reported bug in hardy 8.04 is that when you restart gnome, your 
custom settings in System->Preferences-> Keyboard Preferences-> Keyboard
Layout Options are reset to their defaults.    It's easy enough to switch 
capslock to control manually by typing xmodmap <filename> at a terminal,
where filename contains the lines
    remove Lock = Caps_Lock
    keysym Caps_Lock = Control_L
    add Control = Control_L
However, I can't get this to run as a startup script.   I've defined
a program that runs the xmodmap line, and added the program to 
System->Preferences->Sessions->Startup Programs.  I know the program is
being run at startup but the xmodmap line doesn't work.    There
*must* be an easy way to fix this!   The obvious one would be to
run a .rc file on startup, but I don't know which startup script if any
gnome looks at.    Could anybody please advise?

Thanks, Leo

---

### Post by jrib on 2008-11-23
GNOME should automatically use ~/.xmodmaprc if it finds it.  Check /desktop/gnome/peripherals/keyboard/general in gconf

---

### Post by hictio on 2008-11-23
> 
However, I can't get this to run as a startup script. I've defined
a program that runs the xmodmap line, and added the program to
System->Preferences->Sessions->Startup Programs. I know the program is
being run at startup but the xmodmap line doesn't work. There
*must* be an easy way to fix this! The obvious one would be to
run a .rc file on startup, but I don't know which startup script if any
gnome looks at. Could anybody please advise?

Thanks, Leo


On 8.04, I have done something similar (not mapping CAPS LOCK to Ctrl, but disabling it) by editing, via sudo, the file:

'/etc/X11/xinit/xinitrc'

I have added this (edit it for the Ctrl remap):

```

## Disable CAPS LOCK
/usr/bin/xmodmap -e "remove lock = Caps_Lock"

```

*Before* this line on the file:

```

# invoke global X session script
. /etc/X11/Xsession

```

---

