---
title: "Dual Boot Install XP after Ubuntu"
date: 2009-05-07
forum: General Help
---

### Post by Billsputters on 2009-05-07
Like most people, I was keen to try 9.04 and took the opportunity to tweak the partitions I had on the disc. I now have 

SDA1 20GB ext3 /
SDA5  2GB swap
SDA6 28GB ntfs
SDA7 92GB ext3 /home

As you can see, SDA6 is the intended location of XP Pro.

Installed Ubuntu, setup partitions, copied data back to /home and reinstalled apps - took the best part of a day and all night to get apps as internet is slow here.

Went to add XP and I get the same blue screen as another poster (ee19921) gets. Have a look [here]("http://ubuntuforums.org/showthread.php?t=1146669&highlight=howto+dual+boot")

Anyone any idea how to get around this problem. I really don't want to go back to square one, install XP first, then Ubuntu and then add all the apps and data.

---

### Post by jerrrys on 2009-05-07
you have to install xp first in its own partition. i would use gparted live cd for this. then install ubuntu and it will set up dual boot for you...

---

### Post by Billsputters on 2009-05-07
That really isn't the answer I wanted, but the one I thought I'd get.

OK. So a complete reinstall. Is there anyway I can pull everything off my / and /home partitions, install XP (and screw up the system) and then plonk it all back. I really, really don't want to re-install Ubuntu again. It's not the install, but downloading the apps, which at an average of 7kbs takes a long time.

---

### Post by fermulator on 2009-05-07
Also, Windows is "greedy", and in my experience, always required itself to be on the "first" partition.  XP might have been a little more flexible, but Vista is a monster and refuses anything but the first partition.

You DO NOT have to install XP first.  In your situation, you could:
 1. [https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)
 2.
   * Install Ubuntu (already done for you)
   * Install Windows to the NTFS partition (will overwrite your mbr, no worries)
   * Boot a live CD and:
```
sudo grub
root (hd0,0)
setup (hd0)
quit
```
   * Explained:  "root (hd0,0)" tells grub which partition you want the mbr to point to (i.e. where is grub!), "setup (hd0)" installs the grub mbr pointer to the start of your hard drive (hd0).
   * Edit /boot/grub/menu.list, adding the "Windows Boot" entry:
> title		Windows XP
rootnoverify	(hd0,5)
chainloader	+1

That should work.  Remember, if XP is on /dev/sda6, grub treats this partition as (hd0,5).  Although, you're not showing us the rest of your partitions (i.e. 2,3 and 4th partitions are missing?..)

---

### Post by ELD on 2009-05-07
I installed Windows XP fine after i installed ubuntu, i can't think why it wouldn't work, if windows xp doesn't recognise the partition then it will simply ignore it.
Although come to think of it my XP has always been on the first partition.

---

### Post by Billsputters on 2009-05-07
They are all my partitions. 

SDA1 20GB ext3 /
SDA5 2GB swap
SDA6 28GB ntfs
SDA7 92GB ext3 /home

SDA5-7 are extended, don't know why, that's what the Ubuntu partitioner did during the install. I suppose SDA2 is missing - extended, but I definately do not have a 3 or 4. I've noticed this before and just took is as so.

As the NTFS partition is extended could that be the reason I can't install on it.

---

### Post by cholericfun on 2009-05-07
> **Billsputters said:**
> They are all my partitions. 


As the NTFS partition is extended could that be the reason I can't install on it.

what do you mean - you did install XP no?
oh sorry.. read your post properly
yes- sounds like a problem
i dont see why gparted would have done that though
youre allowed 4 primary partitions on a HD, which you have.
maybe try gparted again...?

---

