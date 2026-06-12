---
title: "Another one of those graphics problems..."
date: 2011-05-23
forum: Desktop Environments
---

### Post by Glupoi652 on 2011-05-23
When I start up my computer, literally nothing is on the screen except for a big "NO SIGNAL" logo.  The only way I can log into Ubuntu is by the sounds the computer makes, and spam pressing the arrow keys until i can log in.  My computer has never done this before, and now I am unable to run 1440x900 resolution... My graphics card is a GTS 450 and I am running Ubuntu 11.04.  

My xorg.conf:  

Section "Device"
        Identifier       "Default Device"
        Option  "NoLogo"         "True"
EndSection

^ Literally, everything that is in that file.  and yes, I did find this in the /etc/X11 folder.

Used to, there wasn't any problem running my computer... It ran on proprietary drivers, no problem what-so-ever @ 1440x900.  Now, the default is the 1024x768.  Please, help me restore my graphics to its previous peace.

---

### Post by Glupoi652 on 2011-05-24
Bump

---

