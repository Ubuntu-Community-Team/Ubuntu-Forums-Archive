---
title: "Gaim system tray startup"
date: 2005-06-02
forum: Desktop Environments
---

### Post by jammupatu on 2005-06-02
Hey all!

1st time Ubuntu user and poster. Switched over from Debian due to XFree / Sarge / i915 bug. I really have to give props, this distro is real good.

Anyways, my problem isn't really Ubuntu specific. I once found a Gaim plugin which made the program start up straight into system tray. Unfortunately I've forgotten it's URL / name... 

Any ideas where to find this plugin?

BR,

-J-

---

### Post by netrattler on 2005-06-02
That feature is already in the Ubuntu version, mine was enabled by default but maybe something happened to yours. Once you sign on to one of your account just click on Tools -> Preferences -> Plugins -> scroll down till you see System Tray Icon and put a check by it. You might have to restart gaim for it to take effect, not sure on that though.

Joe

---

### Post by jammupatu on 2005-06-03
I think you misunderstood me. I want a plugin which starts Gaim straight (and only) into the systray. I've located the plugin once but now I've forgotten it's name.

I've got the normal System Tray Icon plugin. It displays the icon in the systray but it doesn't include the startup feature I'm looking for.

-J-

---

### Post by i-tech on 2005-06-03
You want Gaim to start to run when you login to your system?  then go to System->Sessions->Startup Programs and Add Gaim there.

---

### Post by bored2k on 2005-06-03
[QUOTE=i-tech]You want Gaim to start to run when you login to your system?  then go to System->Sessions->Startup Programs and Add Gaim there.[/QUOTE]
 I believe he doesnt want gaim to popup on bootup. For that you will need Gaim Extended Preferences plugin.

[http://gaim-extprefs.sourceforge.net/](http://gaim-extprefs.sourceforge.net/)

---

### Post by jammupatu on 2005-06-06
Tried to compile the extended prefs but it errors out on 'make'. =( Running Ubuntu 5.04...

UPDATE:

First I found an Ubuntu package but it errors out on libc version. This however installed fine: 
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgaim-extendedprefs%2Fgaim-extendedprefs_0.4-4_i386.deb&md5sum=3aafa8632a2dd2b63a98dbc299628d9a&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgaim-extendedprefs%2Fgaim-extendedprefs_0.4-4_i386.deb&md5sum=3aafa8632a2dd2b63a98dbc299628d9a&arch=i386&type=main)

The feature I was looking for was 'Hide buddy list at signon'.

Thanks a lot!

---

### Post by Ba|der on 2006-10-16
I was looking for the same thing. The addon is now in the repositories and installed with a few clicks in synaptics :)

---

### Post by benjaminzsj on 2006-10-16
I'm using gaim2beta, if you exit without the buddy list showing on the desktop, then no pop up on next startup.

---

