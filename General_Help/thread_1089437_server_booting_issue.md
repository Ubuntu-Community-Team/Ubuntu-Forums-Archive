---
title: "server booting issue"
date: 2009-03-07
forum: General Help
---

### Post by rangester on 2009-03-07
i just added an extra hdd to my server (running hardy), and now it won't boot 'automatically' anymore.

this is where it goes wrong:

```
kinit: no resume image, doing normal boot...
resume: libgcrypt version: 1.2.4
resume: could not start the resume device file /dev/sda5'
        please type in the full path name to try again
        or press enter to boot the system:
```

sda5 is my swap file

when i press enter the system just boots normally, but i want to be able to reboot the server without hooking up a keyboard, as i could do before.

this happened both before and after partitioning/fs-ing/mounting the new hard drive (which is sda, with only an sda1 partition, where my old drive is sdb with partitions sdb 1, 2 and 5)

i'm prolly doing somthing wrong, but i don't know what :-k

[edit]damn, now i re-read my post, i see what's wrong. i guess my old hard drive used to be sda and changed to sdb when i inserted the new disk, but some program still thinks my swap is on sda5 instead of sdb5.
so i guess i'll have to find out what program is wrong, and alter its settings? (would thet program be libgcrypt? i would not know where i can find its settings file :S)[/edit]

---

### Post by Xiong Chiamiov on 2009-03-07
Which drive is /dev/sda got changed when you put in a new drive.  I'd add some [labels](http://wiki.archlinux.org/index.php/Persistent_block_device_naming) to your drives and use those in your /etc/fstab instead.  They make life much easier.

---

### Post by rangester on 2009-03-07
for sda1 and sdb1 adding a label went fine, but for sdb2 (extended(i guess the home folder?)) and sdb5 (swap, the one that caused the trouble in the first place) i get these errors:

```
bas@server:~$ sudo e2label /dev/sdb2 WD80GDATA
e2label: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Couldn't find valid filesystem superblock.
```
```
bas@server:~$ sudo e2label /dev/sdb5 WD80GSWAP
e2label: Bad magic number in super-block while trying to open /dev/sdb5
Couldn't find valid filesystem superblock.

```

what am i doing wrong this time?

[edit]by the way, there is no by-label folder in my /dev/disk folder, only by-id, by-path and by-uuid :S[/edit]
[edit2]i now see that for the swap i need another command, but now i get this error:

```
bas@server:/dev/disk$ sudo mkswap -L SWAP /dev/sdb5
/dev/sdb5: Device or resource busy
``` [/edit2]

---

