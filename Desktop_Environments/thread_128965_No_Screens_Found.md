---
title: "No Screens Found"
date: 2006-02-12
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-02-12
I just installed Kubuntu, but when i was to boot it up, I got this error from the X server. "Fatal: No Screens Found !!"

what the hell am I supposed to do, Im stuck in text mode.


(It worked fine on the same system when I install Ubuntu a few months ago)

---

### Post by Jackel003 on 2006-02-12
I get the same error. I need help on this :-k

---

### Post by stiankarlsen on 2006-02-12
I mean, it can't be my hardware can it? This worked fine on my previous installation with just Ubuntu..

---

### Post by zxee on 2006-02-12
At the comandline do startx or sudo startx and post the output from that. Your xorg.conf must have a problem. You can also do 
'sudo dkpg-reconfigure xserver-xorg' to have the system run the xserver setup.

---

### Post by stiankarlsen on 2006-02-12
I've reconfigured the X server several times, but with no luck. 

Newbie question: How am I supposed to be able to paste the startx output? It's on a different machine, and though I have internet, im in the konsole...

---

### Post by Jackel003 on 2006-02-12
It's not recognzing my card 
-------

Fatal: Error insterting fglrx (/lib/modules/12.6.10-6.17/kernel/drivers/video/fglrx.ko): No Such Device

[fglrx:firegl_init] *ERROR* device not found!
--------

Those are errors I get when I "modprobe fglrx"

I have an ati 850 pro pci-e btw.

---

### Post by stiankarlsen on 2006-02-13
I've done some configuration, and changed ati to vesa, and commented out USEBFDev, as well as the HorizSync and VertRefresh..

The X-server barely starts, and I now get this error: Fatal server error: failed to initialize core devices

---

### Post by short4lif2 on 2006-02-13
do the following

> sudo nano /etc/X11/xorg.conf

And show us what your xorg.conf looks like.

---

### Post by fairyliquidizer on 2006-03-06
i've got this problem too

---

### Post by fairyliquidizer on 2006-03-06
.

---

### Post by fairyliquidizer on 2006-03-06
sorry mine is a failed upgrade to dapper drake.  Should have posted in other forum.

---

### Post by download17 on 2006-10-13
Hey... I have the same problem with Ubuntu 6.06... I can reconfigure the xserver and everything but I can't edit the xorg.conf file...when I use 'sudo nano /etc/X11/xorg.conf' it opens nano but says that it's a new file...HELP... don't know what else I can do...
Luke D.

---

