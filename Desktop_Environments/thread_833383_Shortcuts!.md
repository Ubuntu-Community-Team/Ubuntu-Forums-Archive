---
title: "Shortcuts!"
date: 2008-06-18
forum: Desktop Environments
---

### Post by xtreme- on 2008-06-18
Hi all!
I just discovered that GNOME includes a lot of useful shortcuts, and I though maybe some of you didn't think about this (like me).

By googling a bit, I found some useful ones on [http://vntutor.blogspot.com/2007/10/10-essential-gnome-shortcuts.html](http://vntutor.blogspot.com/2007/10/10-essential-gnome-shortcuts.html) and [http://www.novell.com/coolsolutions/tip/2289.html](http://www.novell.com/coolsolutions/tip/2289.html)

Especially Ctrl-Alt-L to lock screen is nice, and Crtl-Left/Right to switch desktop. Also, I discovered that holding down Shift while pressing enter to open a directory in Nautilus opens it in a new window.

Do any of you have any favourites to share?:razz:

---

### Post by robert.cooper on 2008-06-18
alt g         =    gpodder
alt p        =    pidgin
alt i         =    idle 
alt f5         =    unmaximize
alt v         =    vert max
alt h         =    horiz max
alt scroll     =    window transparency
ctrl alt d     =    DESKTOP
[top left : ]
globe        =    webbrowser FF
letter        =    mail client TB
P        =    mediaplayer QL
[]
ctrl alt n     =     gksu /
alt n         =    /XFS/RobertStuff
ctrl alt s    =    gksu /usr/bin/synaptic
alt w         =    env WINEPREFIX="/home/r/.wine" wine "C:\Program Files\WordWeb\wweb32.exe"
alt s        =    gnome-system-monitor
alt r        =    gksudo -S wifi-radar
alt z        =    rm -rf ~/.local/shares/Trash Empties
ctrl alt h    =    home folder

i like shortcuts to open most common apps.. hate using mouse.
make your own keybindings to do a cmd:
```

gconf-editor

```expand apps>metacity>
select global_keybindings, double click on the run_command number starting at 1 and working your way up. the value should be the keys you want to press to launch the custom command (which we'll enter in keybinding_commands). for control+alt+s (for my synaptic keybinding) i put in 
<control><alt>s
the actual custom command goes in a window below global_keybindings:
expand apps>metacity
select keybinding_command, and double click on the command_<#> to correspond with the values in global_keybindings.
changes take effect immediately, no need to restart gdm or anything like that. try a simple cmd first to make sure your keybind entry is valid, or that's what i do first when debugging.

when i was ripping a ton of cds very often, i found it helpful, if not a little ironic, to make my "windows" key eject.. this was most humorous because i had just switched from vista and was thrilled-with-ubuntu/rueful-at-Micro<hardtolike>soft

---

