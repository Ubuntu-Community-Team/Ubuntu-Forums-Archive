---
title: "Broadcom Wireless LIve cd?"
date: 2008-12-11
forum: General Help
---

### Post by Trzone on 2008-12-11
I was wondering if there was any linux distribution that supported live cd-based support for the broadcome wireless in the HP 6449us laptop.  I am not sure what model it is, but i think it begins with 43 or something to that effect.  Any help would be appreciative. 
Basically i want to be able to use wireless from my laptop without actually going to a wired, it would be quite useful.
Or if anyone would know an article that discusses remastering the live cd to include this, then that would be great as well!

---

### Post by Ayuthia on 2008-12-11
> **Trzone said:**
> I was wondering if there was any linux distribution that supported live cd-based support for the broadcome wireless in the HP 6449us laptop.  I am not sure what model it is, but i think it begins with 43 or something to that effect.  Any help would be appreciative. 
Basically i want to be able to use wireless from my laptop without actually going to a wired, it would be quite useful.
Or if anyone would know an article that discusses remastering the live cd to include this, then that would be great as well!
It would help if you can find the model of Broadcom card it is.  If you are in Linux, you can check by typing lspci -nn in the Terminal/Konsole/xterm window.  The 4311, 4312, 4321, 4322, and some 4328 cards will work with the Broadcom STA (wl) module.  Ubuntu 8.10 comes with it installed.

Otherwise, I don't think that anyone can legally include the proprietary firmware that is needed for the b43 (the open source version) module.

---

### Post by Trzone on 2008-12-11
I think it's the Broadcom 4321ag, i'll download Intrepid and burn it to disk.  Is there a specific package i could download myself and put onto a flash drive and install from there?

---

### Post by Ayuthia on 2008-12-11
If you are referring to downloading packages for the wireless, you should not need anything.  All you need to do is go into System->Administration->Hardware Drivers and enable the Broadcom STA driver (not the b43 option).  After that, it should work.

---

### Post by Trzone on 2008-12-11
Correction, the card is the 4328 supposedly, even though vista says 4321? weird
Anyhow, the Driver does not appear to work from the live cd?
I see h ow you mentioned SOME 4328s
now, how do i make it work? :)

---

### Post by Trzone on 2008-12-11
Just forget about it, it must work with ndiswrapper, broadcom is not a smart company, it's bad publicity :P

---

### Post by Ayuthia on 2008-12-11
You can try and see if the following would activate the card:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```

However, you can always go the NDISwrapper route:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The 4328 card is not officially listed in the Broadcom site for the wl driver, but we have seen a few cards work with the wl driver.  Most likely the Ubuntu developers did not turn on the option for the 4328 card.  However the driver should be in the liveCD because it comes in linux-restricted-modules.

If you have not guessed, the b43 module does not support the 4328 card yet.

---

### Post by Trzone on 2008-12-12
It makes sense to restart the network, i'll have to try that later heh

---

