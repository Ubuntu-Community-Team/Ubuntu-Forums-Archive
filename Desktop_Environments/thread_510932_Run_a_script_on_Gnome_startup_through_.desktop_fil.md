---
title: "Run a script on Gnome startup through .desktop file?"
date: 2007-07-27
forum: Desktop Environments
---

### Post by Metheos on 2007-07-27
Hello, I have several xorg.conf files which I would like to be able to choose from when I log on. I read something about being able to use a .desktop file to call to a script which could cp the appropriate xorg.conf file into action when logging in by choosing the appropriate session type.

I, unfortunately, have no idea how to do this, and my search results have not been of much use. So, if anyone could tell me how to do this, that would be great. Also, what should the script look like? (I've never really made a script before, and I'd prefer not to screw it up.)

---

### Post by zanglang on 2007-07-27
I think copying the files over when logging in would be too late; your X server would have started up and is already halfway to loading your desktop anyway. I'm not sure how would it be possible to intercept startup and present a selection screen (that can potentially lock you out of the system if anything goes wrong). Usually if you'd like to execute scripts on startup, you can add the command into /etc/rc.local, or as a service in /etc/init.d + update-rc.d...

But actually, why would you have multiple versions of Xorg conf files, instead of merging into one good, working, stable conf file?

---

### Post by Metheos on 2007-07-27
Ohh.... "Why" you ask? I'll tell you why! lol
I have 3 monitors running on 2 video cards. Two monitors on an AGP Dual head nvidia 7800 GS, and one monitor on an older PCI Nvidia Geforce MX 440. 

I have THREE different configs I like to choose from.
1. Xinerama, One giant desktop stretched across all three monitors.
2. Not Xinerama, Three separate sessions, one to each monitor.
3. One Monitor, since this is the only setup that lets me use Beryl/etc.

So, yeah. That's why.

---

### Post by zanglang on 2007-07-27
Ow, sure sounds troublesome. :p

Okay, I'll answer your original question first. To make a .desktop file run a command, change its "Exec" line to
> Exec=sh -c "<command you want to execute here>"
The command could be something like
> gksudo cp /etc/X11/xorg.conf.0 /etc/X11/xorg.conf
If you create 3 of the .desktop files it will copy your 3 configurations over nicely, but you'll have to logoff and relogin everytime for it to take effect. Not quite flexible, but is that what you'd like?

---

