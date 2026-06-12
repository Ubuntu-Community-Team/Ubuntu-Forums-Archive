---
title: "Disable GDM/X power saving"
date: 2010-08-24
forum: Desktop Environments
---

### Post by Karl1982 on 2010-08-24
I recently installed the first non-virtual Ubuntu server in our office (to put it in perspective, it's outnumbered several to one by Windows servers).  It had an inexplicable array failure, and now it's been retasked to run VMware Server for testing purposes since we don't trust it at the moment.  For the sake of ease of use, on this server I decided to install Xubuntu desktop x64, rather than Ubuntu server as I've done with a couple others.

This server is on an old school 8-port Linksys PS/2 KVM.  It's got a CRT monitor in the middle of a rack of somewhat aging equipment.  The problem I'm having is somewhere between the KVM, this old monitor, and some power saving... when Xubuntu tries to put the monitor in standby, instead it gets this vertically scrolling garbage.  The Windows servers in this rack don't have any problem putting it to sleep, but I figured I might as well just turn off DPMS on this particular server.

So I logged in via SSH, stopped GDM, generated a /etc/X11/xorg.conf, and changed Option "DPMS" to Option "NoDPMS" which according to the manpage should take care of it.  I also changed the GDM video mode with this xorg.conf so it's definitely being used.  Following some other suggestions I found in my search, I issued "xset s off" and "xset -dpms" but this hasn't disabled monitor power saving either.  I've been restarting GDM each time I change something.  5-10 minutes later it's scrolling garbage again.

What's it going to take to turn off monitor power saving at the GDM logon screen?

---

### Post by Karl1982 on 2010-10-14
I did eventually get this fixed.  Despite what the manpage says...

```
Option "NoDPMS"
```... does not actually work (someone should really fix that).  This does the trick:

```
Option "DPMS" "off"
```

---

