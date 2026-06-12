---
title: "****NO GDM @ 2nd boot****"
date: 2005-10-13
forum: Desktop Environments
---

### Post by piggyaugu on 2005-10-13
I've just installed Breezy from CD.

the first boot is quite tranquille.

Then I did the regular tricks: Add track point scrolling, link my fonts into /etc/fonts/truetype, modify sources.list, modify fonts.conf.

then i gave the 2nd boot.

The gdm kept restarting. and 2min later it stopped for displaying a message.

I logged in as root, restored the original xorg.conf, gdm.conf and did dpkg-reconfigure xserver-xorg.

I tried "startx". It could lead me into gnome. 

and after that I rebooted, the gdm still refused to work. 

What can I do?

P.S. M using a IBM T41 box.

---

### Post by Ampersand on 2005-10-13
When it fails to get into X, it should give you the option to view the log. Could you post the errors from it (should be on the lines starting '(EE)'). If this doesn't work, log in and type 'nano /var/log/Xorg.0.log' and check for errors towards the bottom of the log.

---

### Post by piggyaugu on 2005-10-13
[QUOTE=Ampersand]When it fails to get into X, it should give you the option to view the log. Could you post the errors from it (should be on the lines starting '(EE)'). If this doesn't work, log in and type 'nano /var/log/Xorg.0.log' and check for errors towards the bottom of the log.[/QUOTE]

Well

It seems not quite a X problem. The error message is issued by gdm and it didn't give me a choice to view the log as the X error did.

further more, I can always get into gnome by "startx".

---

### Post by Ampersand on 2005-10-13
What message does GDM give you?

---

### Post by piggyaugu on 2005-10-13
[QUOTE=Ampersand]What message does GDM give you?[/QUOTE]

I cannot make a screenshot. So it was something like " The gdm failed 6 times in the last 2 minutes when it tried to start. I will give another try in 2min(or 90s, cannot remember)" There was only one choice: the "OK" Button.

---

### Post by piggyaugu on 2005-10-13
My GDM log give me these:

I cannot see the problem

```


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux blackbox 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 13 23:33:48 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Synaptics DeviceOff called



```

---

### Post by piggyaugu on 2005-10-13
** Finally I found the problem**


Thanks to the note I've make when I did the modifications.

I make a directory "ttf-myfonts" when I linked the fonts in to /etc/fonts/truetype/

When I removed the directory and rebooted. The gdm come to life. 

I cannot tell why, but it works now.

thx for all the bud's help.

---

