---
title: "StartX problem / recent update hosed install?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by scottylans on 2006-06-22
Hi chaps!

What was in the last big update???

In the past 5 days or so there were some updates released. (quite a few according to the update tool)
My Ubuntu install on my Desktop was nice and solid :( worked fine and now it won't boot, comes up with some nasty x server error or something is not configured  :(

I had a fresh 6.06 install from CD, then all updates up until a week or so ago working fine.
The only stuff I'd installed really was the rt2500 drivers from serialmonkey and the Nvidia drivers from a howto/faq I found here :( 
(and of course all the mandatory stuff to compile the nvidia drivers and RALINK drivers)

I'm figuring it was a change to the graphical engine in the backend which busted the Nvidia drivers :(

Can I still boot into some kind of safe mode or can I umm re-apply the drivers from a console prompt (since I don't get a gui anymore?)

I have basic -> mid range knowledge, so I can wget a new file (assuming the network engine is loaded before the GUI, I'm thinking this is a yes in linux?)

I'll wget a file, untar it compile and install it if someone here can give me some suggestions on what to fix.

Sorry, I'm @ work now so I don't know the precise error, however I can update this post in about 5 hours time with the correct error.
I figure surely someone elses system got hosed too so perhaps you guys know what the problem is and how to fix it.



I beleive this guy might be having the same problem or similar.
[http://www.ubuntuforums.org/showthread.php?t=201541](http://www.ubuntuforums.org/showthread.php?t=201541)

Thanks guys

---

### Post by kaamos on 2006-06-22
> Can I still boot into some kind of safe mode or can I umm re-apply the drivers from a console prompt (since I don't get a gui anymore?)

To get a desktop you can boot in the console (if this doesn't happen automatically press ctrl+alt+F1 after X fails), log in (your password doesn't show any *-symbols when you type it, thats normal) and use the command
```
sudo dpkg-reconfigure xserver-xorg
```
and choose "nv" as your video driver. After that do
```
sudo /etc/init.d/gdm restart
```

This should get you a desktop where it's nicer to work with getting the nvidia drivers to work. The relevant question is, did you install the drivers from synaptic/apt-get or did you download them straight from nvidia?

Hope this helps.

---

### Post by scottylans on 2006-06-22
[QUOTE=kaamos]To get a desktop you can boot in the console (if this doesn't happen automatically press ctrl+alt+F1 after X fails), log in (your password doesn't show any *-symbols when you type it, thats normal) and use the command
```
sudo dpkg-reconfigure xserver-xorg
```
and choose "nv" as your video driver. After that do
```
sudo /etc/init.d/gdm restart
```

This should get you a desktop where it's nicer to work with getting the nvidia drivers to work. The relevant question is, did you install the drivers from synaptic/apt-get or did you download them straight from nvidia?

Hope this helps.[/QUOTE]


Look I MIGHT be wrong but I THINK I deleted the "stock" NV drivers that ship with 6.06 :(

I just followed a howto thread here and yeah I did use the ones direct from nvidia, for better speed / performance in the UI (and they are still so slow!)

Thanks though, I'll take a crack at this tonight.

---

### Post by scottylans on 2006-06-22
[QUOTE=kaamos]To get a desktop you can boot in the console (if this doesn't happen automatically press ctrl+alt+F1 after X fails), log in (your password doesn't show any *-symbols when you type it, thats normal) and use the command
```
sudo dpkg-reconfigure xserver-xorg
```
and choose "nv" as your video driver. After that do
```
sudo /etc/init.d/gdm restart
```

This should get you a desktop where it's nicer to work with getting the nvidia drivers to work. The relevant question is, did you install the drivers from synaptic/apt-get or did you download them straight from nvidia?

Hope this helps.[/QUOTE]



I got an error message :(

"dpkg: conflicting actions --control and --remove"

I appreciate the  help though.

---

### Post by scottylans on 2006-06-22
[QUOTE=scottylans]I got an error message :(

"dpkg: conflicting actions --control and --remove"

I appreciate the  help though.[/QUOTE]


OK!

Here we go BIG POST 


I googled your suggestion and got the exact command.
> sudo dpkg-reconfigure xserver-xorg

I thought there was spaces inbetween  the reconfigure and the xserver-xorg
ANYHOW that bit is solved.
I went through it, chose mostly defaults and nv like you said, re-booted no luck, errors as follows!





> "Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly.
Would you like to view the  server output to diagnose the problem?"


Yes

> 
"X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build operating system: Linux 2.6.12 i686
Current Operatig System: Linux desktop 2.6.15-25-386 #1 PREEMPT Wed
Jun 14 11:25:49 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice (II) informational,
	(WW) warning, (EE) error, (NI) not implimented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 22 18:37:23 2006
(==) Using config file "/etc/X11/xorg.conf"


OK

> 
"Would you like to view the detailed X server output as well?


Yes

(first page, same info)


Page down

OH BOY is there a lot, I'll try to get stuff I think might be relevant.
> 
ServerLayout = default
Screen = default screen
Monitor = Philips 202P
Device = Nvidia Corporation NVIDIA default card

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist

Very bottom

> (EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(EE) Screen(s) found, but none have a usable configuration




OK

> 
"The X server is now disabled. Restart GDM when it is configured correctly."



:(


EDIT!

One quick last thing,
after running "sudo dpkg-reconfigure xserver-xorg" when it's finished I get this message after writing out the config file.

> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2006622185745
It might be nothing, I don't know.

Also I don't know how to

---

### Post by kaamos on 2006-06-22
Hello, and sorry for the delay.

Yes the stock nv driver ships with ubuntu, but it's quite hard to delete it so I don't think you did it by accident. If you did, install the package "xserver-xorg-driver-nv".

Anyway, try "vesa" instead of nv as the driver. After that, I'm out of suggestions. :(

EDIT:
> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2006622185745
this is normal.

---

### Post by scottylans on 2006-06-24
[QUOTE=kaamos]Hello, and sorry for the delay.

Yes the stock nv driver ships with ubuntu, but it's quite hard to delete it so I don't think you did it by accident. If you did, install the package "xserver-xorg-driver-nv".

Anyway, try "vesa" instead of nv as the driver. After that, I'm out of suggestions. :(

EDIT:

this is normal.[/QUOTE]



Thanks for the help, I've ended up completely re-installing again  but now I'm stuck with 2 choices, both bad :(

[http://ubuntuforums.org/showthread.php?p=1171394#post1171394](http://ubuntuforums.org/showthread.php?p=1171394#post1171394)

:(

---

