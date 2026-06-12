---
title: "Updating Graphics Drivers for Games"
date: 2010-05-23
forum: Gaming &amp; Leisure
---

### Post by Axolotl9250 on 2010-05-23
Hello, I am Downloading Regnum Online for Linux (x64) and on their downloads pages suggests going to nvidea's site and getting the latest driver, which for me is for the 8400m GS driver. Now on their website a search brought up this: [HTML]http://www.nvidia.com/object/linux_display_amd64_100.14.09.html[/HTML] which looks like a general one for all thing. But I read somewhere that drivers and things, unlike windows where you search for them and download them (I'm still a relatively new Linux User) and almost kind of bolt them on. In Linux it's part of the kernel (or something) I may be completely wrong but it's just something I read - hence the plug and play sort of ability where you download Ubuntu on a windows laptop and hey presto most things (with a few exceptions) work out of the box. So is downloading this a good idea or am I likely to be up to date (10.04), and will this do anything to the kernel or any part of the OS I don't want to be screwing with. 
I just want to be cautious and not go and ruin anything.
Cheers.

---

### Post by Perfect Storm on 2010-05-24
Use the one that comes with Ubuntu (you'll find the driver under Hardware Drivers).

---

### Post by Axolotl9250 on 2010-05-24
Ok, I had a look at the nvidia website and it said the same - the reason I asked was because Regnum Online is very very jumpy. I looked at this page [HTML]http://www.nvnews.net/vbulletin/showthread.php?t=72490[/HTML] and I understand most of what it wants, especially as when I run the installer it says I must quit the X server and OpenGL applications, and to run in a VGA on this page [HTML]http://us.download.nvidia.com/XFree86/Linux-x86_64/195.36.24/README/README.txt[/HTML]. Now it is this bit that I don't understand or have come across before. I have a suspicion that it's something to do with the GUI of Ubuntu and command line screen but this is very new to me. If anyone can explain further before I go ahead and try anything just so I don't muck up the system I'd be very grateful, if not then it's ok it's more for learning, I still have a quite modern driver from the detect hardware drives function in System->Administration.

---

### Post by portets on 2010-05-24
i recommend waiting for nvidia to release the newer 256.xx series driver. it will include a gui, so you won't have to mess around with configuration files and install it from the command line.

at the moment, it's rather difficult to install the nvidia driver manually in ubuntu 10.04. but the 256 series driver should be nice and easy with just some mouse clicking i presume.

the 256 beta is out, but it doesn't have the gui yet. so i guess just keep a lookout at nvnews.net for their new release

---

### Post by cascade9 on 2010-05-24
> **Axolotl9250 said:**
>  Now on their website a search brought up this: [HTML]http://www.nvidia.com/object/linux_display_amd64_100.14.09.html[/HTML] which looks like a general one for all thing. 

Heh, the old 100.xx driver. Very, very old (june 2007)

> **Axolotl9250 said:**
> Ok, I had a look at the nvidia website and it said the same - the reason I asked was because Regnum Online is very very jumpy. I looked at this page [HTML]http://www.nvnews.net/vbulletin/showthread.php?t=72490[/HTML] and I understand most of what it wants, especially as when I run the installer it says I must quit the X server and OpenGL applications, and to run in a VGA on this page [HTML]http://us.download.nvidia.com/XFree86/Linux-x86_64/195.36.24/README/README.txt[/HTML]. Now it is this bit that I don't understand or have come across before. I have a suspicion that it's something to do with the GUI of Ubuntu and command line screen but this is very new to me. If anyone can explain further before I go ahead and try anything just so I don't muck up the system I'd be very grateful, if not then it's ok it's more for learning, I still have a quite modern driver from the detect hardware drives function in System->Administration.

Seriously....just do it the way that Artificial Intelligence suggested (system-> administration-> drivers) 

The drivers you get from there are the 195.36.15 version. Which isnt quite the newest (that is 195.36.24) but its the 2nd newest, and any perfromance difference will be minimal.....if there is any at all. 

Current version in 10.04-

[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

As for why you need to use a command line to install the drivers from nvidia, its because you cant install the nVidia drivers with 'X' (the desktop gui) open. 

If you are having issues with how 'jumpy' Regnum Online is, I wouldnt be suprised if that was because the 8400GS is a long way from a gamers card. That is a guess. You could always try turning down detial, textures, etc and see if that helps. ;) 

@ portets- interesting, they are jumping to 256.xx..and its meant to have a GUI installer (eventually I spose). I wonder if they are going to have another driver 'break' with the 195.xx drivers becoming GF6-toGF9 (or GT2XX) and the 356.XX drivers will end up being only cards newer than that? ;)

---

