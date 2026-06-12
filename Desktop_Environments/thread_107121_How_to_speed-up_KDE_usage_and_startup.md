---
title: "How to speed-up KDE usage and startup?"
date: 2005-12-22
forum: Desktop Environments
---

### Post by simone.brunozzi on 2005-12-22
Hi,
I have kubuntu 5.10, with KDE. I also installed Easy Ubuntu to have the most useful plugins and stuff.

I was wondering if you know a guide, a quick tutorial, or a thread in this forum, in which I can have help to speed-up KDE; I mean, be able to use less memory and less CPU, for example taking away unuseful services, or similar things.

Any help is greatly appreciated! Thanks

Simone

---

### Post by HermanAB on 2005-12-22
Whatever tweaks you make won't help much.

The only solution to having a faster GUI is to use a different one, eg. IceWM.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by Adrian on 2005-12-22
[QUOTE=simone.brunozzi]Hi,
I have kubuntu 5.10, with KDE. I also installed Easy Ubuntu to have the most useful plugins and stuff.

I was wondering if you know a guide, a quick tutorial, or a thread in this forum, in which I can have help to speed-up KDE; I mean, be able to use less memory and less CPU, for example taking away unuseful services, or similar things.

Any help is greatly appreciated! Thanks

Simone[/QUOTE]

I always disable all animations and remove the background picture. Some people say that disabling the desktop icons helps too. On my 800MHz Celeron laptop, this configuration feels pretty fast (noticably faster than Gnome actually).

There is a wizard in KDE that lets you adjust the performance by moving a slider (i.e. select the amount of resource-demanding eye candy to use). I don't know what it's called, but it is run by default whenever you do a clean KDE install (i.e. not kubuntu-desktop). I think it popped up when I installed the "kde" meta package (which some people prefer to "kubuntu-desktop"). I don't think that it's selectable through the menus, but you can probably run it if you know the name of it... (anyone?)

Edit: After some googeling, I found out that it's probably called "kpersonalizer". I can't verify it now though.

---

### Post by ltmon on 2005-12-22
[http://wiki.kde.org/tiki-index.php?page=Performance%20Tips](http://wiki.kde.org/tiki-index.php?page=Performance%20Tips)

L.

---

### Post by Adrian on 2005-12-22
[QUOTE=ltmon][http://wiki.kde.org/tiki-index.php?page=Performance%20Tips](http://wiki.kde.org/tiki-index.php?page=Performance%20Tips)

L.[/QUOTE]

Very nice. Thanks!

---

### Post by dejitarob on 2005-12-22
You could also try [prelinking]("http://ubuntuforums.org/showthread.php?t=74197")

---

### Post by simone.brunozzi on 2005-12-23
Thanks everybody, very useful tips and hints.
I'll try them now.

Merry Xmas!

cheers,

---

### Post by funkyou on 2005-12-23
What i have done to speed up my KDE-Desktop:

**System:**
-New Kernel with cK-Patch + CPU optimization
-Prelinking
-Tuned some Kernel parameters like swappiness
-Disabled all unessecary services
-Optimized DMA for disks

**Xorg:**
-Activated Composite, even when you do not use the FX, it speeds up a lot

**KDE:**
-Deleted many fonts i do not use
-Using only one font for KDE, and another for the Konsole
-Told KDE that it is prelinked
-Disabled all KDE services i do not use

In my opinion, (K)ubuntu would gain a good if not massive speedup, 
if the developers optimize the packages and kernel for i686 etc like 
yoper does...

My System is a Athlon XP 1600 with 512mb and nVidia GF5200FX-LE,
and i think its quite fast :)

---

### Post by simone.brunozzi on 2005-12-30
funkyou,
can you provide some details about :

New Kernel with cK-Patch + CPU optimization

thanks!

Simone

[EDITED]: Sorry, I found it already:

[http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174)

thanks!

---

