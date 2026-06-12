---
title: "iPod help"
date: 2005-11-26
forum: Desktop Environments
---

### Post by tazzik on 2005-11-26
Hi,
My ubuntu 5.10 works great however, my iPod mini 2g 4GB is not recoginesed. It does not show on the desktop and in the "filesystem" where it says "Apple iPod music player" if I click on that it says it is unable to mount it. On the extra info part it says there is a bad superblock on /dev/sdb. But when I go to /dev there is no sdb folder there. Shouldn't the iPod be listed in /media/iPod anyway? What I want to know is how to see the iPod, not put music on it but to use it as another HDD, in iTunes on windows, the enable disk use box IS checcked.
Cheers
tazzik

---

### Post by tazzik on 2005-11-26
*bump*

---

### Post by jmeadows111 on 2005-11-26
Is your Ipod formatted for Fat32 or HFS? If the latter you may have issues unless you have an HFS driver installed; Fat32 is much easier. Some [useful info]("http://pag.csail.mit.edu/~adonovan/hacks/ipod.html")

---

### Post by astoltz on 2005-11-26
I've got a few idea on where to start looking - no particular order.
Does it work OK in windows - if yes, the rest of this may not be much use.
What does dmesg say after you plug in the ipod?
Did you try dosfsck (or chkdsk in windows)?
How do you know the ipod is getting assigned /dev/hdb?  Do you have another   device using /dev/hda?
did you try to manually mount it?  (mount -t vfat /dev/hdb)

---

### Post by tazzik on 2005-11-27
dmesg says 
[4333984.212000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4333984.228000] FAT: bogus logical sector size 2
[4333984.228000] VFS: Can't find a valid FAT filesystem on dev sda.
[4333984.247000] FAT: bogus logical sector size 2

hope this helps

---

### Post by angkor on 2005-11-27
[QUOTE=tazzik]dmesg says 
[4333984.228000] VFS: Can't find a valid FAT filesystem on dev sda.
[/QUOTE]

Did you format your iPod on a windows box?

---

### Post by tazzik on 2005-11-27
yes i did format it on windows and i have chkdisk it and it says its fine. Should I re-format it?

---

### Post by astoltz on 2005-11-27
Before reformatting, try ```
sudo dosfsck -r /dev/hda
```  That link by jmeadows111 back in post #3 is a good one - you might read through that if you haven't already.  If the dosfsck doesn't help you could try reformatting from Ubuntu following the steps in that link.

---

### Post by tazzik on 2005-11-27
this is the output:
tayo@ubuntu:~$ sudo dosfsck -r /dev/sdb2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb2: 11 files, 11/986065 clusters
(its sdb2 btw not hda)
i have reformatted but still doesnt work
but it works in windows

---

