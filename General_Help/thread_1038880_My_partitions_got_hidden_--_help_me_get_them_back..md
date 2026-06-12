---
title: "My partitions got hidden -- help me get them back."
date: 2009-01-14
forum: General Help
---

### Post by theWrkncacnter on 2009-01-14
Hello all,
I tried to install Windows 7 on a logical partition, but the installer exited almost immediately, encountering an error.
As I went to install the Windows 7 beta, my partitions were something like this

[Windows XP]  [{30gb empty} {/ 10gb} {/home 140gb} {/boot 200mb}] [swap]

[] for primary, [{}] for extended/logical

now it looks like this

[Windows XP][180 gb empty][swap]

So it looks like even though the installer saw the extended and logical partitions, it tried to write itself to the extended partition, but luckily failed. So my data should still be safe and not written over.

What can I do to restore the partitions as they should be?
Thanks,
Patrick

---

### Post by chex_m8 on 2009-01-14
I don't really understand what it is you want.
you said: "What can I do to restore the partitions as they should be?"
what do you think the partitions should be?
they appear fine to me.

---

### Post by theWrkncacnter on 2009-01-14
The whole extended partition I had ubuntu on now appears to be empty space
it went from 
[{30gb empty} {/ 10gb} {/home 140gb} {/boot 200mb}]
to
[180 gb empty]. This is what I see with gparted on a live cd now.

I need to turn the empty space back into the extended/logical partitions I had before.

I hope that helps!

---

### Post by theWrkncacnter on 2009-01-14
Failing getting my partitions back, the next best thing would be to recover the data that is hidden in the "empty space," not yet written over. Are there programs which do this? Thanks.

---

### Post by dagnabit dang doohickey on 2009-01-14
You may want to try a partition table restore utility. Several years ago I successfully restored a completely wiped MBR using the commercial Windows software called Partition Table Doctor. There's opensource software available that can do this, such as [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), but I haven't had the need to use such software since, so I can't give any usage experience.

---

### Post by theWrkncacnter on 2009-01-14
Thank you! I will try this

---

### Post by caljohnsmith on 2009-01-14
TheWrkncacnter, if you want some specific help with using testdisk to try and recover your lost partitions, how about trying these steps:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

**If you are using Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by theWrkncacnter on 2009-01-14
Alright -- I had already done things a little differently -- I chose "log" and stopped after quick search. But I'm running it again this time following your directions. The only difference is I'm using the windows version since I can still boot into it using super grub disk.

---

### Post by theWrkncacnter on 2009-01-14
[IMG]http://img181.imageshack.us/img181/2668/testdiskresultsph7.png[/IMG]

partitions 1,3,4,5,6,7 have directory listings, although I don't know how it is possible for me to have two linux homes.
I also don't know why swap is set as primary bootable. that doesn't seem right.

Right before I tried to install Windows 7, I shrank the linux home partition and moved it further down on the hard drive. So the first linux home that shows up *might* not be the real one, but how can I be sure?

---

### Post by caljohnsmith on 2009-01-14
OK, based on the start/stop cylinders of your partitions, and based on which partitions gave you a directory listing, I think you should mark them as follows:
```

1 *
2 D
3 L
4 L
5 L
6 D
7 L
8 L
```
It looks like the only ambiguity is whether your true home partition is the 5th or 6th partition listed; when you select each of the home partitions and do "p" to get a directory listing, how about using the right arrow key to navigate to your home directory, and by looking at the files determine whether your home partition is the 5th or 6th partition listed (it can't be both of course). So if you determine that the 6th partition is actually your home directory, you can mark the 5th partition with "D" and the 6th partition with "L" instead. Also, in case testdisk won't let you mark one or more of the partitions above with "L" that I've shown marked as "L", mark those partitions with "P" instead. Once you're sure you have all the partitions marked correctly, press enter to get the next screen where you can write your new partition table. Then reboot, and please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by theWrkncacnter on 2009-01-15
i am having a little trouble booting up into linux as grub is still borked. I'm trying to get it back with sgd. Right now, I see my correct grub menu, but when I choose ubuntu I get error 15 cannot find file or something like that.

---

### Post by caljohnsmith on 2009-01-15
You don't happen to have a Ubuntu Live CD (the install CD) that you can boot? Without that, it might be really difficult to get back into your Ubuntu install unless you are really lucky.

---

### Post by theWrkncacnter on 2009-01-15
I do. Booted it up, ran fdisk

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x696f696f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    92052449    46026193+   7  HPFS/NTFS
/dev/sda2        92052513   482415884   195181686    f  W95 Ext'd (LBA)
/dev/sda3       485243325   488392064     1574370   82  Linux swap / Solaris
/dev/sda5        92052576   114077564    11012494+  83  Linux
/dev/sda6       114077628   136102679    11012526   83  Linux
/dev/sda7       178080588   481885739   151902576   83  Linux
/dev/sda8       481885803   482415884      265041   83  Linux

```

---

### Post by caljohnsmith on 2009-01-15
OK, probably the best thing to do would be to go through all your linux partitions and see if everything is OK. First though, how about trying to reinstall Grub:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hd0,X) where X is a number, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hd0,X)
grub> setup (hd0)
grub> quit
```
Then mount your linux partitions:
```
sudo mkdir /media/sda{5,6,7,8}
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sda6 /media/sda6
sudo mount /dev/sda7 /media/sda7
sudo mount /dev/sda8 /media/sda8
nautilus /media &

```
The last command will pull up a file browser with the /media directory showing; how about going through sda5 through sda8 in the media directory and get some idea of what is there and what might be missing. Let me know how that goes.

---

### Post by theWrkncacnter on 2009-01-15
Thank goodness all my files are in order (nautilus recognizes them and mounts them if you click on them). One interesting thing is one of the partitions I deleted to make room for windows 7 has been reincarnated (sda6). 

Getting grub back installed
```
grub> find /boot/grub/stage1
 (hd0,5)

grub> find /grub/stage1
 (hd0,7)

```
one of these, I think, is the /boot partition, the other one is not right. According to gparted, my boot partition is /sda8. so I reinstalled (hd0,7). Will restart shortly

---

### Post by theWrkncacnter on 2009-01-15
Same error 15: File not found. Grub is still not working.

grub entry details:
```
root (hd0,6)
kernel /vmlinuz-2.6.27-9-generic root=UUID=54bf4403-2c21-41be-94fe-8443b815ae10 ro quiet splash boot: noapic no1apic
initrd /initrd.img-2.6.27-9-generic
quiet
```
could this perhaps be out of date; needed to be upgraded?

---

### Post by caljohnsmith on 2009-01-16
How about posting the output of:
```
sudo mkdir /media/sda{5,6,7,8}
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sda6 /media/sda6
sudo mount /dev/sda7 /media/sda7
sudo mount /dev/sda8 /media/sda8
ls -l /media/sda{5,6,7,8}
```

---

### Post by theWrkncacnter on 2009-01-16
You got it. It's rather long, so it's in the pastebin rather than the forum thread. But I could post it here if that would be better.
[http://paste.ubuntu.com/105716/](http://paste.ubuntu.com/105716/)

---

### Post by caljohnsmith on 2009-01-16
In the Grub entry you posted, how about changing the (hd0,6) line to (hd0,7), since (hd0,7) is your boot partition:
```
root [COLOR="Blue"](hd0,7)[/COLOR]
kernel /vmlinuz-2.6.27-9-generic root=UUID=[COLOR="Blue"]54bf4403-2c21-41be-94fe-8443b815ae10[/COLOR] ro quiet splash boot: noapic no1apic
initrd /initrd.img-2.6.27-9-generic
quiet
```
Also, check that the UUID above in the kernel line is for the sda5 partition, because it appears that sda5 is the Intrepid root partition. You can check the UUIDs with:
```
sudo blkid -c /dev/null
```
Let me know if booting with the above entry works or not.

---

### Post by theWrkncacnter on 2009-01-16
Yes, changing root to (hd0,7) absolutely worked! I don't know how the boot partition changed from being /dev/sda7 to sda8, but it works now. And the UUID is correct for sda5. Thank you!

Now I'm backing up and repartitioning to give Windows 7 a nice primary partition to install to :)

Thanks for all of your help!

---

### Post by caljohnsmith on 2009-01-16
Glad to hear that worked OK; hope your Windows 7 install goes smoothly too. Cheers and have fun with all your OSes.

---

