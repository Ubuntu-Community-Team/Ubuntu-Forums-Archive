---
title: "Display resolution during boot"
date: 2008-01-03
forum: Desktop Environments
---

### Post by nadrach on 2008-01-03
I have Kubuntu 7.10 loaded on a 6-yr-old AMD 800 Mhz self-built machine with an Asus 9200 video card to a Fujitsu Siemens C384FA-M monitor, native 1024x768 resolution. The live CD worked fine, but after install, the boot display for Kubuntu with the boot progress bar, is presented at display settings outside the range of the monitor. Things correct when the login screen is presented after X starts. This stage is OK on the live CD, with the display settings correctly detected and presented; but not after install. My guess is that GRUB has been configured with an initial display setting outside the monitor range. Any suggestions as to why?

---

### Post by AnonCat on 2008-01-03
I'm not on my Ubuntu machine right now and can't give you more detailed information at this moment, but I fixed that problem on my computer by editing the resolution in the xorg.conf file.  One of the lines in that file (under "display" I believe) will show a list of resolutions.  Put the resolution you want as the first one in that list, or alternatively, delete the other resolutions and only leave the one you want.  I can give you more info once I have access to my Ubuntu computer.  In case your wondering, you can find xorg.conf in the /etc directory.  I'm not familiar with Kubuntu, but typing  sudo gedit /ect/xorg.conf  in the terminal might open the file for editing for you.

---

### Post by nadrach on 2008-01-03
I've confirmed that "xorg.conf" has an erroneous first display setting of "1280x1024", but removing it from the file has no effect. The boot procedure is still getting the higher resolution setting, before X is started. X is OK in normal  running, it correctly sets to 1024x768 from the graphical login screen, onwards. The "xorg.conf" file is created by dpkg from settings elsewhere, which are what appear to be used during the initial boot sequence. If I run "dpkg-reconfigure", as shown within "xorg.conf", it reinstates the "1280x1024" resolution from somewhere, and it is that somewhere that I think needs to be modified.
The only quirk that I did find, after removing the "1280x1024" value from "xorg.conf", is that when a forced check of the hard drive was triggered (after 23 mounts), the boot display dropped into a visible text display (it appeared to be 800x600 aliased to full screen on the LCD) until the filesystem check completed, and then went back to 1280x1024 ("out of range"); until X started for the login window.

---

### Post by erfahren on 2008-01-03
this guide explains it well
[http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970)

---

### Post by nadrach on 2008-01-03
OK, followed all the advice, been round the houses, and nailed down to the splash screen. Whatever VGA code I used that was valid for the monitor, worked, but only for text displays during boot. The culprit that persists in displaying "out of range" is the splash screen, both in boot-up and shutdown. Kill the splash and the problem disappears. Unfortunately, this leaves me with a blank screen during most of the boot and shutdown, which is OK by me, but there are other users of the system who are less tech-savvy, and get worried by long seconds of nothing (I'm training them ... slowly) and seeing something would be helpful. My guess is that the splash screen picks up a resolution from similar or same configuration source that "xorg.conf" uses to reconfigure, which has 1280x1024 as a permitted resolution (which is invalid for the Siemens LCD). Any suggestions as to where to look/modify would be greatly appreciated.

---

### Post by AnonCat on 2008-01-03
You can change the splash resolution by editing the usplash.conf file.  I believe that is the file name, but I also had to change the resolution in that file for splash screen to display correctly.  I'll look on my Ubuntu computer and give you more info if you need it.  I think that file is also in the /etc directory, but I need to look to be sure of both the name and directory.  I'll get back to this later today.

---

### Post by erfahren on 2008-01-03
for the usplash.conf see this: [http://ubuntuforums.org/showpost.php?p=3741687&postcount=21](http://ubuntuforums.org/showpost.php?p=3741687&postcount=21)
(you have to do the "sudo update-usplash-theme usplash-theme-ubuntu" thing too)

---

### Post by nadrach on 2008-01-03
Yo! We are cooking with charcoal! Fixed ... thank you very much.

---

