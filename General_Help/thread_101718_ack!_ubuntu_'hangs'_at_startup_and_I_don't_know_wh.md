---
title: "ack! ubuntu 'hangs' at startup and I don't know what to do..."
date: 2005-12-10
forum: General Help
---

### Post by Makrie on 2005-12-10
Hi, and thanks for reading...

**The problem:**
When I restart my computer it does all its checks, gets to the brown screen with a rectangular 'ubuntu' logo thing and stays there. I can move the pointer using the mouse and turn on and off caps and number lock.

**The system:**
It's a Dell Poweredge 700 with mirrored SCSI's and a SATA drive. It used to work fine!

**What I can remember I've done since last successful restart that may have messed it up:**
Installed TOR and priv something as per 'browse anonymously' thread on this forum.

Changed permissions on /usr/share/fonts to allow anyone to write to it.

Stuck a folder containing subfolders containing about 30,000 fonts into /usr/share/fonts.

Any and all help gratefully received.

Thanks again, Makrie

edited to say I'm able to write this cause I've got another couple computers... (all Windows)

edited again to say pretty much fixed!

---

### Post by aysiu on 2005-12-10
When I experienced this problem using a live CD on a friend's laptop, it was a screen resolution thing, so that's always worth a shot.

Try Control-Alt-F1, logging in, and then ```
sudo dpkg-reconfigure xserver-xorg
``` and disable the higher resolutions (800 x 600 should be pretty safe).

---

### Post by Makrie on 2005-12-10
Okay... just done that, reset resolution successfully by the look of the hung start screen - but it's still hung...

are there any other possible fixes? I'm kinda relieved I can get to a command line!

---

### Post by taurus on 2005-12-10
Since the last thing you installed before all this happened, could it be related to the fonts that you installed???  Maybe you want to look at your /etc/X11/xorg.conf to make sure it points to where the fonts are.

---

### Post by Makrie on 2005-12-10
**Thanks to you both!**

I'm now back in, having deleted the folder of many fonts I'd stuck in /usr/share/fonts... think I'll post a new thread about fonts!

Thanks again, feels great to be okay!

Makrie

---

