---
title: "KDE 4.2, dual display, big desktop on ATI Radeon 9600"
date: 2009-02-24
forum: Desktop Environments
---

### Post by markofealing on 2009-02-24
Yesterday my Dell Latitude C640 laptop updated itself, I recall seeing something flash up about KDE 4.2 but it didn't register until today when I discovered a different looking desktop and a broken widget (the yellow thing that looks like Post It Note (c)!)

I have to say I think the colour scheme is an improvement and the screen tearing when menus are displayed looks like it has been fixed. Overall I like the improved look of the desktop.

Unfortunately, yesterday I dumped Kubuntu on my desktop after the KDE4.1 trashed xorg.conf using the ATI 9.2 drivers, in favor of Ubuntu and Gnome who's support for dual display and "big desktop" actually works on a ATI Radeon 9600 card out of the box using open source drivers! Maybe I should give KDE4.2 a second chance?

Anyone with any KDE 4.2 experience on an ATI Radeon 9600 with dual display and big desktop?

Should I go for open or propriety ATI 9.2 drivers, which work best?

---

### Post by Ubuntiac on 2009-02-24
My card's an HD4850 not a 9600, but on Intrepid, the fglrx drivers and 4.2 worked with big desktop beautifully.

Then I upgraded to Jaunty and remembered FGLRX doesn't isn't supporting Xserver 1.6 yet... *sigh*

Bizzarely, Blender seems to work just fine on the ATI driver. Huh? I though R700 cards weren't supported for full 3d yet?! :popcorn:

---

### Post by th0th696 on 2009-03-01
I've got a HD 3650 (R635 I believe), on a dual core amd 64 with 4 gigs of ram,  and out of Studio64, UbuntuStudio 32bit, Kubuntu 64 bit, Mythbuntu 32 bit, Gentoo 64 bit, Crunchbang 32 bit only the "vesa" drivers seem to work consistently.  I had 8.542 proprietary ati drivers working in Gentoo at first, but then I get cocky and tried to upgrade to all the other possibilities in the portage tree with no luck, so I tried kubuntu's restricted driver application that pops up on the right hand corner (envyng-qt), no luck as it wouldn't install properly from the GUI.  So I pop out a terminal and do a 
```

sudo envyng -t
```

for the text mode envy, that installs no problem, reboot not looking so hot.  So I try the 9.2 proprietary drivers, and I got it to work by letting it install the drivers (the .deb package it made didn't work either).  Now the login screen comes up garbled, same result when I ran the installer in gentoo.  ATI drivers are a mess at the moment, I'm just glad they are opening up, hopefully soon we will have some quality open source drivers.  Back to "vesa" on the buntu's, and 8.542 on gentoo for me.

---

