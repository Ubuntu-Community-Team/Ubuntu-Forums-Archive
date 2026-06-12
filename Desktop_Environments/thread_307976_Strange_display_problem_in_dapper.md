---
title: "Strange display problem in dapper"
date: 2006-11-27
forum: Desktop Environments
---

### Post by nematode on 2006-11-27
Hi, hope someone can help me with this.

Im running dapper on a Compaq D310 which uses the intel 82845G/GL with a HannsG HW191D screen which has a native res of 1440x900

After a fair amount (I wont say how much as its embarrassing) of work Ive got  a 1440x900 desktop, sort of.

The leftmost 2 inches of the display (from the speaker icon) and the bottom inch and half are unusable. They will just fill with colour when a window in dragged in to them.

Im using 915resolution to re-map video modes

#! /bin/sh

/usr/sbin/915resolution 58 1440 900 32 1904 932
/usr/sbin/915resolution 49 1440 900 16 1904 932
/usr/sbin/915resolution 38 1440 900 8 1904 932

exit 0

I've also attached my xorg.conf.

I get no errors logged, and my Dell which uses the Intel 945 chipset works fine.

I've tried about everything I can think of to fix this, so any suggestions gratefully received.

---

### Post by nematode on 2006-12-13
Update

I havent done much on this lately (I'm waiting for all the replies to roll in :) )

But I have noticed that if I play video it is corrupted. I basically get 2 sets of images side by side just showing grainy strips of video. I dont know if this gives anyone any ideas as to what the problem is.

---

### Post by nematode on 2006-12-27
More out of hope than anything else, Ive blown away my Dapper install and installed Edgy.

No difference.

I cant be the only person in the world with this problem so if anyone has any ideas please reply.

](*,)

---

### Post by lavs23 on 2007-02-09
I have this exact same problem.  I'm running at a different resolution then native right now.  I've ran several other different distros that work with 1440x900 the last one I remember was Mandriva One 2007.  I'm still trying to figure out what's going on.

---

### Post by joey on 2007-03-06
I'm currently experiencing this exact problem.

---

### Post by elexhobby on 2007-03-14
So, I'm not alone.. I too get this grainy screen, especially while running firefox.. Does nobody have a solution to this?

---

### Post by joey on 2007-03-14
In my particular instance this appears to be a machine type specific error ...probably bios. I have some folks working on this for me.

---

### Post by joey on 2007-03-15
"Fixed" for me. The answer was rather simple but it only works if you have a laptop. :-) 

During the boot cycle, hit the button which switches between LCD and External display such that only the external monitor is running.  When you get to k/gdm go into a console and run sudo dpkg-reconfigure xserver-xorg  (no -phigh).  Follow the configure but choose the simple method for determine refresh rate.   Recycle GDM and try it.  In my case, the only resolution which worked was 1280x1024.

---

