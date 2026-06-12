---
title: "CIF Single Chip cheapo webcam"
date: 2009-01-01
forum: General Help
---

### Post by The Joe on 2009-01-01
I would like to use my webcam with Skype. However all I get is some fuzzy green-ness. Just some green-static like effect.

I don't know the exact model, it's a cheapo one from Woolworths (hah).

Is there any specific driver/software/whatever I need to be able to get a clear picture?

---

### Post by The Joe on 2009-01-04
Heh. Dropped it and broke it anyway, cheap little thing...

---

### Post by stewsnooze on 2009-03-14
I have this same cheap webcam. I would like it to work. Has anyone got it going?


Linux blackbuntu 2.6.27-11-generic #1 SMP

---

### Post by ProNux on 2009-03-14
In my case, I got my camera working on Kopete by installing the following

libjasper1
libjasper-dev
libjasper-runtime

You might try to install and see if it works.  By the way I am on Ubuntu 8.04 Hardy Heron.

---

### Post by catanzag on 2009-03-21
I got the same problem and I solved finding solution in comments from [bug #260918]("https://bugs.launchpad.net/ubuntu/intrepid/+source/vlc/+bug/260918"). You have to run skype with LD_PRELOD of libv4l, typing ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
``` after eventually install ```
sudo apt-get install libv4l-0
```

regards

catanzag

---

### Post by areskz on 2009-07-12
Thanks, that worked for me!

---

### Post by latev on 2009-08-02
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Didn't work for me - any ideas?
I'm running 64 bit Ubuntu

In gstreamer-properties the camera works fine - I just can't get it to work in Skype

---

### Post by catanzag on 2009-08-05
I don't have 64-bit ubuntu, but I found in the previous cited [bug #260918]("https://bugs.launchpad.net/ubuntu/intrepid/+source/vlc/+bug/260918") that you need both the 32-bit and 64-bit versions of the library due to the fact that Skype is 32-bit. So you have to run skype with LD_PRELOD of libv4l, typing ```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
``` after  installation with ```
sudo apt-get install lib32v4l-0 libv4l-0
```.

Hope this can help you

regards

catanzag

---

### Post by latev on 2009-08-05
Yep - I already found that solution couple of days ago, thanks anyway!

---

### Post by terrykiow on 2011-09-01
I have both the cheapo Asda CIF webcam CP-68L and the more sophisticated Microsoft Lifecam vx6000.  I can get neither of them to work with Skype, and that is the main reason I need a webcam.

So far I have tried all the remedies recommended here without success.  I am using an HP Compaq 6720s with 160gb hdd and 2gb RAM.  It was formerly an XP laptop, but not anymore!!!

Please help if you can.

T:guitar:

---

