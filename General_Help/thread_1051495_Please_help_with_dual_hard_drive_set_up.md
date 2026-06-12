---
title: "Please help with dual hard drive set up"
date: 2009-01-26
forum: General Help
---

### Post by audio_uphoria on 2009-01-26
Hello, I have a question about finding windows programs in linux. I have two hard drives set up on my computer and linux is installed on one hard drive which is the master and windows is installed on the second drive which is the slave.  My question is, in linux, how can I view all the files on the windows hard drive? I have ubuntu 7.10 and the windows is 98 I believe. Please help. Thanks.

---

### Post by semi_fiction on 2009-01-26
If the drive is not shown under the "places" menu (as "xGB Media"), post the output of this in a terminal:
```
sudo fdisk -l
```

---

### Post by audio_uphoria on 2009-01-26
Thanks for the quick reply. It doesnt show up in the places menu and I've tried looking all around in my system files with out any luck. I'm still trying to get used to the linux gui and it's file system is different than what I'm used to. Here's what comes up after I put in sudo fdisk -l:



Disk /dev/hda: 4310 MB, 4310433792 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         494     3968023+  83  Linux
/dev/hda2             495         524      240975    5  Extended
/dev/hda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/hdb: 4324 MB, 4324368384 bytes
144 heads, 63 sectors/track, 931 cylinders
Units = cylinders of 9072 * 512 = 4644864 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         931     4222984+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(929, 143, 63) logical=(930, 143, 63)

---

### Post by semi_fiction on 2009-01-26
Ok, now try this in a terminal:
```
sudo mount /dev/hdb1
```
Now, if it says something like "cannot find /dev/hdb1 in fstab or mtab", or you want it to mount automatically at startup do this:
In a terminal type:
```
sudo gedit /etc/fstab
```
then add this line to the bottom of the document, you can copy and paste it:
```
/dev/hdb1 /media/WindowsDrive vfat defaults 0 0
```
Save and exit the document, then exit the terminal.

---

### Post by audio_uphoria on 2009-01-26
As you can see they're both very small drives. It looks like the windows drive is fat32, can linux read that? Also I noticed that partition 1 has different physical/logical endings. Is that bad?

---

### Post by audio_uphoria on 2009-01-26
Ok, it couldn't mount from the terminal so I pasted the code into the bottom of the document. I restarted linux and i still don't see it.

---

### Post by semi_fiction on 2009-01-26
Well, I assume that is has to be the different physical/logical endings issue, what that means is that Ubuntu doesn't recognize your windows partition layout as valid. The only solution I can offer is to back up all your important Windows files, then do a low-level(not "quick") format and reinstall Windows, and replace your files. That's kind of a last resort thing, so I'd wait and see what information other people have to offer first. :)

---

### Post by audio_uphoria on 2009-01-26
Ok, thanks for your help. I plan on formatting the windows drive so linux can use it anyway so I can have a whopping 8gb storage space (my flash drive has more memory). lol. My next task is to try and set up a small linux server with this if possible just so I can get some experience not to actually use it. Thanks again.

---

### Post by audio_uphoria on 2009-01-27
Does anyone have any other suggestions on how I can view my hard drive?

---

