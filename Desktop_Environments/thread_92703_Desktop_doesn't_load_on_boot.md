---
title: "Desktop doesn't load on boot"
date: 2005-11-20
forum: Desktop Environments
---

### Post by kilovh on 2005-11-20
I have just installed Breezy Badger. I boot my computer up, it gives me a pretty splash screen and tells me its loading modules etc. Everything works okay. The splash screen dissapears, and I'm left with a black screen with a blinking cursor that after a few seconds freezes. IF I press enter at this point, I hear drum sounds from my speakers.

I'm using an Nvidia Geforce 5200 video card.

THanks for your help in advance.

---

### Post by taurus on 2005-11-20
Sounds like it is having a problem either with your video card or your monitor!!!  Wait for the system to finish booting.  Then hold down the <Crtl> & <Alt> while hitting F2.  Log in at the prompt and have a look in /var/log/Xorg.0.log to see what's the problem.  For now, I would recommand you use "nv" (generic) for your nVidia in /etc/X11/xorg.conf.  You can edit your /etc/X11/xorg.conf with 

sudo pico /etc/X11/xorg.conf
-or-
sudo vi /etc/X11/xorg.conf (if you don't have pico on your machine...)

and make sure this line looks like this,

Driver          "nv"
 
Save it and reboot...

---

### Post by kilovh on 2005-11-20
This unfortunately didn't solve the problem; in fact now it seems there are new ones. After I get the flashing cursor, the login prompt comes up for a moment and then the screen goes blue and an error box pops up, saying that there is a problem with xorg.conf.

The important lines from the error log, as far as I could tell, are:

(WW) NV: NO matching device section for instance (BusID PCI:1:0:0) found
(EE) No Devices Detected.
Fatal Server error: No screens found.

It then tells me to restart when xorg is configured correctly, and leaves me at the login prompt.

I'm beggining to wonder if this problem has anything to do with the fact that I have three graphics cards in my computer: The NVidia, which is the one that works and that I always use, an old ATI card that broke a couple of years ago, and the generic onboard SIS chip. WHy I think this has something to do with it is because in xorg.conf, it *identified* the graphics card as "ATI RADEON" etc.

Once again, thanks you for your time.

---

### Post by taurus on 2005-11-20
[QUOTE=kilovh]
I'm beggining to wonder if this problem has anything to do with the fact that I have three graphics cards in my computer: The NVidia, which is the one that works and that I always use, an old ATI card that broke a couple of years ago, and the generic onboard SIS chip. WHy I think this has something to do with it is because in xorg.conf, it *identified* the graphics card as "ATI RADEON" etc.

Once again, thanks you for your time.[/QUOTE]
Is your old broken ATI card an PCI?  Why not remove it since it's no good anyway.  And for onboard video card, you can disable it from your BIOS...  And if your system thinks you have an ATI video card, you cannot use "nv" for it!  Why not change that line to "vesa" and see what happen.  Again, if you can, remove the ATI and turn off the onboard video card so you will only use your nVidia card.

---

