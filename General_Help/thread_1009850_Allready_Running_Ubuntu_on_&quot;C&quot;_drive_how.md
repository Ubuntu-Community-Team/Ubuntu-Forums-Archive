---
title: "Allready Running Ubuntu on &quot;C&quot; drive how do I load Vista on &quot;D&quot; drive?"
date: 2008-12-13
forum: General Help
---

### Post by Trancegonadz on 2008-12-13
I'm fairly new to the world of linux and have very little idea where to start when it comes to creating a partition for linux on the same machine but on a different hard drive. 

Currently both of my hard drive partitions are for Ubuntu 8.10 but Ubuntu is only loaded on one of the hard drives. My hope is that I would be able to load Vista on the second hard drive. Then when I start my computer up it will give me the option to boot either hard drive "Vista" or hard drive "Ubuntu". 

If someone could just point me in the correct direction or if anyone knows a good tutorial, your services would be greatly appreciated.

Thanks ahead of time,
Brad

P.S. - I allready backed up the GRUB info on a disc just in case if I mess up.

---

### Post by Feeriswheel on 2008-12-13
You can add following information in the "menu.lst" which is in the /boot/grub/.

"root" is stander for the dirve of Operating System. The example is show the first drive (hd0,0),the second drive is (hd0,1) and so on.

#examples
#
 title         Windows 95/98/NT/2000
 root          (hd0,0)
 makeactive
 chainloader   +1

---

### Post by Zimmer on 2008-12-13
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by caljohnsmith on 2008-12-13
If you boot the Ubuntu drive on start up, and your Vista is on the only other drive, then you could use the following type of entry in your Grub's menu.lst to boot Vista:
```
title       Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
That assumes Vista is in the first partition of the second boot drive. If you would like more specific help, how about posting the following after you have installed Vista:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by Trancegonadz on 2008-12-14
I still can't get Vista to install, so that I can dual boot Vista and Ubuntu!!!!!

Problem: Windows Vista Ultimate install disk will not recognize any partitions that I have made in the GRUB partition editor, which was partitioned from a Ubuntu 8.10 64 bit install disk.

What I did: Started Ubuntu 8.10 64 boot disk. Selected "Run Ubuntu without installing". Went to the "partition editor" partitioned Ubuntu to approx 20 GB and left open approx 200 GB for the vista install (on the same Hard Drive).
Restarted System
Loaded Windows Vista Ultimate install disk. Got to "Custum" install and the installer couldn't recognize that there were any partitions. 

With a little further investigation I discovered that Windows installer thought my hard drive was a removable disk drive.

Any Ideas???

~Brad

---

### Post by Zimmer on 2008-12-15
I think you may need to format the 'unallocated' space to NTFS before Vista will recognise it..

---

