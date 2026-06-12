---
title: "Multimedia keys not working at startup"
date: 2009-01-17
forum: General Help
---

### Post by petehall on 2009-01-17
I have a Microsoft Multimedia Keyboard 1.0A. I'm using 8.10 Intrepid.

Most of the multimedia keys worked fine "out of the box" with the exception of "My Pictures", "My Music", "Messenger" and "Log Off" which had unrecognised codes.

I have put the following in bootmisc.sh:

setkeycodes 0xe4 191
setkeycodes 0xbc 192
setkeycodes 0x85 193
setkeycodes 0x96 194

I have also set up an appropriate xmodmap.conf in my home directory, and then set suitable values in apps > metacity in gconf-editor so that the keypresses will fire off the appropriate command. However, they don't work on startup. If I open up gconf-editor and change one of the values in apps > metacity > global_keybindings (it doesn't even have to be one of the four keys above - any keys will do) then suddenly all four keys work as desired.

Any help would be appreciated.

Thanks

Pete

---

### Post by petehall on 2009-01-18
bump.

---

### Post by petehall on 2009-01-19
I'm going to bump this one last time, but it's looking like no-one here knows how to solve my problem.

---

### Post by petehall on 2009-01-20
Resolved - from what I can gather, having the xmodmap.conf in my home directory was meaning that it was called too late in the process, apparently after all the gconf settings were loaded, so the bindings weren't being set up. Loading up the xmodmap.conf at an earlier stage (ie in /etc/gdm/PostLogin/Default) means that everything works as it should.

Thanks for all the assistance.

Pete

---

### Post by ridgeland on 2009-01-27
Thanks petehall,
I only wanted to change the Caps_Lock to a Tab key.
I created /etc/gdm/PostLogin/Default as a bash script with execute permissions for all.  In the script it just runs
xmodmap /Path/Xmodmap.CAPSLOCK
/Path/Xmodmap.CAPSLOCK has only the two lines:
remove Lock = Caps_Lock
keysym Caps_Lock = Tab

---

