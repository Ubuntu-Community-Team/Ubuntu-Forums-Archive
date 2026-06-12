---
title: "Just a thought, but serious... (About MediaDirect 3)"
date: 2008-01-13
forum: Dell  Ubuntu Support
---

### Post by JangMunho on 2008-01-13
I'm now faced with the problem that when I press the MD3 button, the partition table will be destroyed... Then I search the forum for an answer, all I got was using "sudo dd if=/dev/zero of=/dev/sda". It seems that though I've reparted the hard drive, it still contains a small hidden partition for MD3, which I'll never see through either PQMagic or Gparted.

I recalled a question I've tried asked in this forum, but never did I get a correct answer, that is everytime I shutdown the laptop, the value of "Power-Off_Retract_Count" (a value in S.M.A.R.T which shows how many time you have shut down your hard drive incorrectly) will add 1. 
I was told it was a bug of the kernel. I tried the instruction posted in the thread, but never did it work. I even compiled a new kernel, but still no effect at all. And now, I reparted the hd, and installed ubuntu 7.10, the problem seems still stand there, smiling at me.

I wonder if Media Direct 3 does something with the hard drive problem. If so, I must use that dd command to get rid of MD3...
Or if you guys can give me another method to disable the md3 button so that I don't need to reinstall ubuntu? (Installing an OS is boring and annoying)

Thank you!!!

Here is the result of "sudo fdisk -l":
```

mingo@mingo-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       19457   141637072+   5  Extended
/dev/sda5            1825       11550    78124063+  83  Linux
/dev/sda6           11551       15197    29294496   83  Linux
/dev/sda7           15198       16413     9767488+  83  Linux
/dev/sda8           19203       19457     2048256   82  Linux swap / Solaris
/dev/sda9           16414       19202    22402611   83  Linux

Partition table entries are not in disk order

```

---

### Post by syxbit on 2008-01-30
that's the only way
the MD3 is in an HPA (protected area)
dd is the only way to remove it AFAIK

---

### Post by Rhubarb on 2008-01-30
It may be possible to use HDAT2 to get rid of the HPA.
[http://www.hdat2.com/](http://www.hdat2.com/)

The HDAT2 forums are here:
[http://www.getphpbb.com/phpbb/?mforum=lcabla](http://www.getphpbb.com/phpbb/?mforum=lcabla)

---

