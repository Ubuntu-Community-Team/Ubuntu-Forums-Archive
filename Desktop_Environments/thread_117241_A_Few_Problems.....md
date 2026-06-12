---
title: "A Few Problems...."
date: 2006-01-14
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-01-14
I hope no one minds, but thanks to all the help here i've gotten my system where i can use most things i need to, but not everything so i thought I'd include the last couple of things into one thread to see if anyone has some answers rather than clutter up the forum.

My Dvd's won't play.  I get an error about lbdvdcss.  I have no idea where to install this from.  I'm trying to play them in Totem for now.  I did a search and installed all the win32 codecs from the mplayer page,  I can play mpegs and avi files just fine.  But no dvds.

VLC will not play sound. No error message.  It'll play all the video files it's supposed to, but no sound.

Flash animations will also, not play sound.  I'm speaking of animations through Firefox.  I do have Flashblock plugin installed, but sometimes there's animations i need/want to interact with.

I've installed the upgrade to firefox (kinda amazed i did it without asking for help, laugh away ;) ) But the old version is still on my system.  I have no idea where the folder is located or how to uninstall apps.  I would also like to know how to edit the menus in Gnome (Applications, Places, System) so stuff isn't listed there that i don't want or need.  

Thanks for your time :)

---

### Post by amohanty on 2006-01-14
> My Dvd's won't play. I get an error about lbdvdcss. I have no idea where to install this from. I'm trying to play them in Totem for now. I did a search and installed all the win32 codecs from the mplayer page, I can play mpegs and avi files just fine. But no dvds.

Add the plf repos to your /etc/apt/sources.list
> deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free


Then do a: > sudo apt-get update
sudo apt-get install libdvdcss

Once you are done comment out the above lines by adding a # at the beginning of the lines.

> VLC will not play sound. No error message. It'll play all the video files it's supposed to, but no sound.

Flash animations will also, not play sound. I'm speaking of animations through Firefox. I do have Flashblock plugin installed, but sometimes there's animations i need/want to interact with.

Have you been able to get sound working on your system?
Also I have noticed that sometimes adblock may block your flash, even though you have clicked on the flashblock thingy. Try disabling it for the site you want to see/interact with and see if that works.

HTH
AM

---

### Post by aysiu on 2006-01-14
[QUOTE=DigitalDuality]
My Dvd's won't play.  I get an error about lbdvdcss.  I have no idea where to install this from.  I'm trying to play them in Totem for now.  I did a search and installed all the win32 codecs from the mplayer page,  I can play mpegs and avi files just fine.  But no dvds.[/quote] Download [this](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb) to your desktop, then open a terminal and type ```
cd Desktop
sudo dpkg -i libdvdcss2_1.2.9-0.0_i386.deb
```

> 
Flash animations will also, not play sound.  I'm speaking of animations through Firefox.  I do have Flashblock plugin installed, but sometimes there's animations i need/want to interact with. See the first link of my signature. Then open up a terminal and type ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree flashplayer-mozilla
```

> 
I've installed the upgrade to firefox (kinda amazed i did it without asking for help, laugh away ;) ) But the old version is still on my system.  I have no idea where the folder is located or how to uninstall apps.  I would also like to know how to edit the menus in Gnome (Applications, Places, System) so stuff isn't listed there that i don't want or need. The proper way to install 1.5 is here:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

