---
title: "Resizing partitions"
date: 2009-03-06
forum: General Help
---

### Post by Von-Dyke on 2009-03-06
[Solved]

I'm currently dual booting Windows XP and Ubuntu 8.10 on a 500gb hdd. 400gb is dedicated to XP and 100gb to Ubuntu, but i want to reverse that; keeping 100gb for XP LAN Gaming pretty much; thereby knowing that all Windows games are going to work perfectly at LAN Parties, etc.
But is there a way to do this without losing Data, or should i backup;format;partition?

---

### Post by cyclone5uk on 2009-03-06
How recently did you install Windows? If it was a while back you’ll need to de-frag it a couple of times first. Then just run the Gparted live CD from boot and it’ll let you shrink/grow whichever partitions you want.

You can get Gparted here: [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

There’s always some risk involved, so it would be wise to backup your personal data just in case. I’ve used Gparted before and never had a problem though.

---

### Post by Von-Dyke on 2009-03-06
The installation is from about June/July last year, but i defragged on a regular (fort-monthly) basis... Still wise to defrag, disk cleanup and other general moving about on it i imagine?

---

### Post by Von-Dyke on 2009-03-06
> **cyclone5uk said:**
> 
You can get Gparted here: [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")


Just reading through that page it says 

GParted Live is a small bootable GNU/Linux distribution for x86 machine.


x86 machine? This doesnt mean a 64-bit machine does it..? I'm running 32 Bit (I think...).
I might be illustrating a void in my pc knowledge right now, but is this of concern?

---

### Post by cyclone5uk on 2009-03-06
X86 refers to the chip architecture, not the processor type. You can run Gparted on your 32-bit machine no problem.

The reason I mentioned the defragging is because it will give you more potential room to shrink your Windows partition. Defragging physically organizes the contents of the disk to store the pieces of each file close together and contiguously. It also attempts to create larger regions of free space using compaction.

So run a defrag in Windows, then boot from the Gparted live CD. You&#8217;ll need to download the ISO image for Gparted then burn it onto a CD. After that you&#8217;ll need to make sure your computer will boot from CD. You can change that setting in the bios.

Here is a guide for how to use Gparted:

[http://gparted.sourceforge.net/larry/livecd/livecd.htm]("http://gparted.sourceforge.net/larry/livecd/livecd.htm")

And another specifically about resizing partition:

[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

If any of this sounds too technical or confusing just stop and post back here. It&#8217;s better to ask questions than try and do something without all the answers!

---

### Post by cyclone5uk on 2009-03-10
I was wondering if you'd had any luck resizing your partitions? If so could you mark the thread as "solved"?

Thanks

---

### Post by Von-Dyke on 2009-03-10
Yep, everything worked out as you said. Thanks for all the help.

---

