---
title: "Dual Monitor... 2nd monitor always disabled!"
date: 2009-04-29
forum: General Help
---

### Post by RAMWolff on 2009-04-29
Hiya,

I'm running a dual monitor set up and I really would love a solution to getting that second monitor set up correctly so it's on when I boot into Ubuntu.  I'm in Vista right now so I can get to the Device Manager to let you know my card name and all that.  

By the way, is there a "Device Manager" in Ubuntu??  I'm running 9.04

Monitors are both ViewSonic and the card is a  NVIDIA GeForce 9800 GT  pretty nice card. Quad core system with 8 gigs of RAM.  

Anyway, when I boot into Ubuntu I only have the one monitor on.  I bring up the X Server since the default GeForce driver reports that it can't do what I need it to do or something like that so then I get another message asking me if I would like to use the NVIDIA X Server and I say "yes" and up it pops.  Seems to have all that I need. 

I see my 2nd monitor is disabled.  So I enable it and set it up so it's "To the Right" so that it's an extention of my first monitor.  I test this by moving my cursor over to the 2nd monitor.  That checks out fine.  I do a little more tweaking and then try to save the file and I get an error message saying that that bak file can not be created so I'm not even sure that the updated settings are being saved either because when I boot back in low and behold the 2nd monitor is disabled again!!  

ARGHHHHHHHHHHHHHHHHH!  :lolflag:

Please help! 

Thanks.  

Richard ;-)~

---

### Post by kanikilu on 2009-04-29
Try running nvidia-settings as root:
```
gksu nvidia-settings
```
This should allow you to save the configuration file.

Also, as for your question regarding a "device manager" for Ubuntu, try installing **gnome-device-manager** or just run ```
sudo lshw -html > ~/Desktop/lshw.html
``` and open the resulting html file in Firefox.

---

### Post by RAMWolff on 2009-04-29
Thank you so much.  I really appreciate your advice.  

Richard ;-)~

---

