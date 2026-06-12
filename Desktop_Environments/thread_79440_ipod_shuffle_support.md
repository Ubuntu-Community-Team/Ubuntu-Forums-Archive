---
title: "ipod shuffle support"
date: 2005-10-20
forum: Desktop Environments
---

### Post by duffman25 on 2005-10-20
Hi

I'm thinking about buying an ipod shuffle (1GB) & I was wondering how was breezy support out-of-box for it. In particular, does breezy's rhythmbox support it? does the banshee player in universe support it? or do I have to install gtkpod?

Thanxs, any experiences will be usefull.

---

### Post by GrumpyBob on 2005-10-20
I use gtkpod with an iPod nano.  I rip CDs with grip.  The problem I have is with ejecting the iPod from the USB port...
yamipod ([www.yamipod.com](www.yamipod.com)) is another possibility, but I found it a bit buggy, at least on a Hoary box.

Robert

---

### Post by rickwood on 2005-10-20
I use Ubuntu with my iPod Shuffle (512 MB).  I've also used Ubuntu to transfer songs to my wife's iPod Shuffle (1 GB).  When you plug it in it shows up on the desktop, just like a USB thumbdrive.  Hence, you can easily use it as both a USB drive for data storage as well as a music player.  I tried several programs for loading music to it, and have had the best luck with gtkpod.  However, gtkpod seemed kind of buggy when it scanned my music library (~3,500 songs).  It crashed several times.  However, once that was done, it's worked without issue.

When I initially bought the Shuffle I set it up using my wife's WinXP machine.  I'm not sure how you would originally format it under linux (perhaps gtkpod or some other linux sofware handles this as well, but I figured using WinXP would be a more sure bet).

For buying music, I use iTunes running under VMware.  However, I haven't yet figured out how to make VMware talk to my iPod (it sees it, but tells me that a linux driver is already controlling the device).  Anyway, I use JHymn to strip out the DRM.  Then I can use the file just fine in Juk, as well as transfer it to my iPod with gtkpod.

I haven't even looked to see if rhythmbox or banshee will support it, so I can't answer those questions.  But I did try the version of Amorak shipped with Breezy with no luck.  It doesn't seem to recognize when the iPod is mounted.  I even tried mounting it in another location (i.e., the default location Amorak is expecting), but that didn't help either.

---

### Post by duffman25 on 2005-10-20
[QUOTE=rickwood]I use Ubuntu with my iPod Shuffle (512 MB).  I've also used Ubuntu to transfer songs to my wife's iPod Shuffle (1 GB).  When you plug it in it shows up on the desktop, just like a USB thumbdrive.  Hence, you can easily use it as both a USB drive for data storage as well as a music player.  I tried several programs for loading music to it, and have had the best luck with gtkpod.  However, gtkpod seemed kind of buggy when it scanned my music library (~3,500 songs).  It crashed several times.  However, once that was done, it's worked without issue.

When I initially bought the Shuffle I set it up using my wife's WinXP machine.  I'm not sure how you would originally format it under linux (perhaps gtkpod or some other linux sofware handles this as well, but I figured using WinXP would be a more sure bet).

For buying music, I use iTunes running under VMware.  However, I haven't yet figured out how to make VMware talk to my iPod (it sees it, but tells me that a linux driver is already controlling the device).  Anyway, I use JHymn to strip out the DRM.  Then I can use the file just fine in Juk, as well as transfer it to my iPod with gtkpod.

I haven't even looked to see if rhythmbox or banshee will support it, so I can't answer those questions.  But I did try the version of Amorak shipped with Breezy with no luck.  It doesn't seem to recognize when the iPod is mounted.  I even tried mounting it in another location (i.e., the default location Amorak is expecting), but that didn't help either.[/QUOTE]


Thanxs for your information :)

---

### Post by objorkum on 2005-10-20
[QUOTE=GrumpyBob]I use gtkpod with an iPod nano.  I rip CDs with grip.  The problem I have is with ejecting the iPod from the USB port...
yamipod ([www.yamipod.com](www.yamipod.com)) is another possibility, but I found it a bit buggy, at least on a Hoary box.

Robert[/QUOTE]

Have you tried "sudo eject /dev/sda" (if sda is your iPod)?

And yes, iPods work fine in GNU/Linux (gtkpod is great).

---

### Post by ddonky on 2006-02-24
[QUOTE=rickwood]I use Ubuntu with my iPod Shuffle (512 MB).  I've also used Ubuntu to transfer songs to my wife's iPod Shuffle (1 GB).  When you plug it in it shows up on the desktop, just like a USB thumbdrive.  Hence, you can easily use it as both a USB drive for data storage as well as a music player.  I tried several programs for loading music to it, and have had the best luck with gtkpod.  However, gtkpod seemed kind of buggy when it scanned my music library (~3,500 songs).  It crashed several times.  However, once that was done, it's worked without issue.

When I initially bought the Shuffle I set it up using my wife's WinXP machine.  I'm not sure how you would originally format it under linux (perhaps gtkpod or some other linux sofware handles this as well, but I figured using WinXP would be a more sure bet).

For buying music, I use iTunes running under VMware.  However, I haven't yet figured out how to make VMware talk to my iPod (it sees it, but tells me that a linux driver is already controlling the device).  Anyway, I use JHymn to strip out the DRM.  Then I can use the file just fine in Juk, as well as transfer it to my iPod with gtkpod.

I haven't even looked to see if rhythmbox or banshee will support it, so I can't answer those questions.  But I did try the version of Amorak shipped with Breezy with no luck.  It doesn't seem to recognize when the iPod is mounted.  I even tried mounting it in another location (i.e., the default location Amorak is expecting), but that didn't help either.[/QUOTE]


This program works great with the Shuffle. I've tried using most of the gui programs and they seem like overkill for the display-less iPod Shuffle.

[http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

---

### Post by dudus on 2006-04-25
I like the gnupod-tools. They're in the repos. They're cli based but was the only one that worked for me.

Never tried this shuffle-db though... maybe I'll try this

---

### Post by ddonky on 2006-05-18
I use 'sudo eject ipod' to umount my shuffle. 

Sometimes it takes a couple of minutes for it to actually unmount though. You'll know it's ok to remove when the light stops blinking and you get the command line back.

I have mixed results when I use the "right click on the iPod desktop icon, and drag down to unmount' method.

---

### Post by tallganglyguy on 2006-05-18
[QUOTE=rickwood]For buying music, I use iTunes running under VMware.  However, I haven't yet figured out how to make VMware talk to my iPod (it sees it, but tells me that a linux driver is already controlling the device).  Anyway, I use JHymn to strip out the DRM.  Then I can use the file just fine in Juk, as well as transfer it to my iPod with gtkpod.[/QUOTE]
If your device is unmounted this should work just fine in VMWare. I have had issues doing this with a mounted iPod, but unmounted volumes worked just fine.

---

### Post by 3rdalbum on 2006-05-19
Why not get another flash-based player that doesn't require a music database? Sandisk make some good ones, that are quite reasonably priced. Heck, you can go for a cheapie if you like, most of them still use the usb-mass-storage driver that is supported by Ubuntu.

And after you get such a player, e-mail the manufacturer to tell them it works with Ubuntu :-)

---

