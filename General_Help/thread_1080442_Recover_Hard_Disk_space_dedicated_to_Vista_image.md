---
title: "Recover Hard Disk space dedicated to Vista image"
date: 2009-02-25
forum: General Help
---

### Post by staf0048 on 2009-02-25
A while back in put Ubuntu permanently on my laptop and everything has been running (mostly) perfectly.  So I'm happy with that.  I have an 80 GB HDD, that came pre-installed with Vista and there was about 10 GB dedicated to the Vista image, which caused the HDD to appear to only have 70 GB capacity.  I assumed it was on a partition that I couldn't touch as it didn't give me another drive letter for it. 

So, when I installed Ubuntu, the intstall recognized all 80 GB (I think it was something more like 79.5 actually) and I used the entire HDD to install the system.  However, once installed it only recognized the 70 GB capacity (same as when Vista was installed).  I don't understand why Ubuntu wasn't able to wipe out that partition (if that is indeed what's happened) and am looking for a way to recover that disk space without re-installing the system again.  

Any thoughts?

---

### Post by handy on 2009-02-25
Boot up your Ubuntu LiveCD (as a LiveCD free's your boot system from any responsibility) & call GParted from the LiveCD.

After which you will get to see what is going on with  your HDD.

You can then extend the size of the partition, or whatever takes your fancy.

---

### Post by staf0048 on 2009-02-25
I have gparted installed on my system - will it work without booting from the live cd or do I have to not be running from the HDD to get it to work?

---

### Post by kahlil88 on 2009-02-25
I'm almost 100% certain the hard drive can't be in use. Oddly enough though, Mac OS X v10.5 "Leopard" will let you partition from within the OS...I hope GNU Parted gets this feature soon!

---

### Post by caljohnsmith on 2009-02-25
How about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
That will tell us how you have your HDD partitioned, and maybe explain why it seems to be only 70 GB.

---

### Post by staf0048 on 2009-02-25
Hehe - I'm retarded!!

I completely forgot that I encrypted my HDD since it's a laptop.  I normally just put it to sleep instead of shutting down and restarting (which I know makes my reasons for encryption useless), so the encryption made a partition which took up some space, plus I have a 3 GB swap.  It all adds up now.

---

