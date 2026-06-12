---
title: "Display Issues"
date: 2010-03-31
forum: Desktop Environments
---

### Post by Cabs21 on 2010-03-31
OK first some background.

Took old compaq desktop running XP and installed ubuntu 9.10 32-bit.  Upgraded the P4 3.06 Ghz to a P4 3.0 Ghz w/ HT.  Added 750 Mb of ram to the original 512 Mb.  The MoBo has an integrated graphics card and and VGA output.  The MoBo manual can be found [here]("http://www.elhvb.com/mboards/OEM/HP/manual/grouper_manual.pdf").

The issue I am having is that when I plug the desktop into my 15" LCD or 17" CRT monitors the resolution is at a normal amount (1280x1024) but when I plug in the desktop to the 47" TV I can not get higher then 800x600.  I have tried connecting my laptop to the TV and was able to get almost 1360x900, or something close to that, so I know the TV can output the higher res.  I also was able to detect the TV as another monitor.  The desktop labels the TV as "Unknown" and gives it the standard save resolution.  Can anyone help me to tell my desktop what it is connected to and up the resolution.  I am looking to purchase an Nvidia PCIe 2.0 x16 video card in a few months but I would like to get this system up and running before I spend money on it to beef it up.  Thanks

---

### Post by Grenage on 2010-03-31
It will be an EDID issue, are you able to download an EDID file for that TV?  If you have another cable, give that a go.  I would personally configure all the settings in xorg.conf.

---

### Post by Cabs21 on 2010-03-31
> **Grenage said:**
> It will be an EDID issue, are you able to download an EDID file for that TV?  If you have another cable, give that a go.  I would personally configure all the settings in xorg.conf.

I have HDMI cables that I prefer to use BUT the computer does not have HDMI outputs until I buy a newer better graphics card.  It could be an EDID issue I will have to look into that.  I am not sure I know how to or what to change in this case.  I am guessing I will have to make a backup copy and then go into the xorg.conf file and manually change the res by force and then reboot.

---

### Post by Grenage on 2010-03-31
Some *modelines* will probably take care of it.  If you are swapping between monitors then it might be a bit of a pain, but you can use metamodes (I think they are called that) to toggle between them.

For example; at home I often don't have the TV on, bit the computer monitor is always in use.  Some apps also have issues with twinview, so I use metamodes to disable the second screen.

---

### Post by Cabs21 on 2010-03-31
> **Grenage said:**
> Some *modelines* will probably take care of it.  If you are swapping between monitors then it might be a bit of a pain, but you can use metamodes (I think they are called that) to toggle between them.

For example; at home I often don't have the TV on, bit the computer monitor is always in use.  Some apps also have issues with twinview, so I use metamodes to disable the second screen.


I am not using this as a dual monitor mode.  I have been setting up the system and gathering programs and settings on other monitors that have LAN connection near by.  I plan to finish updating and editing settings then connect to the TV permanently to the computer as a monitor for the desktop and use it to watch digitally stored media from hard drives.  currently the desktop is being moved around just to set it up the way I like it.

---

### Post by Grenage on 2010-03-31
Ah that's handy, you won't need to much around too much.  I'd personally go with modelines; if we were to treat the TV issue as a standard EDID display problem, I have a [guide]("http://www.grenage.com/xorg.html") that might help you.

---

