---
title: "Screen Split Following Software Update Is A Driver Foul-Up"
date: 2014-06-14
forum: Desktop Environments
---

### Post by TheJetman on 2014-06-14
Hello all.  Installed Lubuntu 14.04/32 yesterday in a VMWare VM for eval purps.  Not a newbie, as I've installed and tweaked earlier iterations of Ubuntu w/o incident.  This time, I simply added some stuff from the Lubuntu Software Center, then ran Software & Updates.  After the system rebooted, the desktop was split !

[It's Broken]("http://s19.postimg.org/hrswwqu4j/Lubuntu_Desktop_2014_06_14_18_53_56.png")

Never seen this before.  Poked around in the hidden folders, but nothing jumped at me as a file I should obviously look at, altho this affects both of the users I've setup, I haven't where global settings for LXDE are kept (bec I've never encountered a malfunction before.)  So far, I haven't found anything on GOOGLE, so I'd appreciate suggestions.  TIA...

More info:  The title bar of a maximized window stretches across the entire display and the right-most controls are visible and fu7nctional.  The left side of the window is duplicated, just like the desktop icons shown.  Any attempt to manipulate the left side of the window, corrupts the center of the display until its useless.  Just start over ???

Even More Info:  It's the display driver update, which is almost certainly part of the kernel update, which occurred during this massive transaction.  I partially confirmed my suspicions by rebooting and calling up the GRUB menu for recovery mode.  Instead, I chose the previous kernel installation and I'm typing this message just fine....  Moreover, while waiting for feedback from the forum or a stroke of inspiration, I tried installing LXLE in another VM.  I checked 'Install Updates During Installation' and after that 1st reboot, the LXLE desktop display showed the same "features" as Lubuntu.

Can always start over and perform the update via Synaptic, which would give me complete control over what is installed.  But is the kernel update really to blame ???

---

