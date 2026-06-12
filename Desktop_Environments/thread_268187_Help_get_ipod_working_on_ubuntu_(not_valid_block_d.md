---
title: "Help get ipod working on ubuntu (not valid block device)"
date: 2006-09-29
forum: Desktop Environments
---

### Post by samssf on 2006-09-29
I have tried the popular tutorials online on how to get this to work. However, when I try to mount my ipod, I receive the error "sdd2 is not a valid block device". And yes, I know that sdd2 is the correct partition that I need to use, and have set it up in fstab.

Any help is appreciated.

---

### Post by brucevangeorge on 2006-09-29
I have had MAJOR problems with my pod. Which one is yours?

I got a 1st gen nano working on mine.

---

### Post by samssf on 2006-09-29
mine is the 5th gen I believe (30 gig video)

I just need to get it to mount =(

---

### Post by samssf on 2006-09-30
bump...

---

### Post by smahomad on 2006-09-30
Hi, I'm at the same stage using a 60Gb iPod video

I'm planning on using it with banshee

---

### Post by infol on 2006-09-30
Please note that the Ipod needs to be formatted in (wonderful) Windows to set the correct fs before you can mount it in Ubuntu..

---

### Post by lawina on 2006-09-30
My ipod is probably fourth generation(20GB). When i attach it to the newly installed Dapper Drake, Rythm box pops up but does not play any songs.
How i downloaded GtkPod (thanks synaptic) and its able to see the songs and call xmms externally to play the same.
Is there any reason why Rythm box is not able to play my iPod?

---

### Post by smahomad on 2006-09-30
The iPod has been formatted in windows, and is working just fine under windows.

I just can't seem to mount it or whatever needs to be done for it to be used by music apps (in my case banshee)

---

### Post by brucevangeorge on 2006-10-03
1st try the Ipod HOWTO.

If that doesn't work... this is how I got my nano to mount properly: [http://www.ubuntuforums.org/showthread.php?t=269135](http://www.ubuntuforums.org/showthread.php?t=269135)

It's kind of a last resort thing.

---

### Post by redmansk8 on 2006-10-03
my Ipod nano (2gig) mounted fine the first time I used it. It took me awhile to find a program that works with it. The program I found that works best is banshee.

---

### Post by moore.bryan on 2006-10-03
*ipods are pains in the tuckus in linux b/c of apple's marketing strategy.  my nano 5gen 4gb never worked right... put [rockbox]("http://www.rockbox.org") on it and now just manage via [gnome-commander]("http://www.nongnu.org/gcmd/") or [xfe]("http://roland65.free.fr/xfe/").*

---

### Post by vandal47 on 2008-04-06
I had a similar problem where my iPod would (seemingly) randomly stop talking to ubuntu and I would get the "invalid block device message". After trying all of the hard stuff, I switched to a different usb port on my computer and everything worked fine after that.

---

