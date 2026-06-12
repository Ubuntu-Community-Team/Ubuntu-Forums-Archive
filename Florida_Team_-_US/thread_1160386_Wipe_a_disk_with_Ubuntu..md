---
title: "Wipe a disk with Ubuntu."
date: 2009-05-15
forum: Florida Team - US
---

### Post by aliencure on 2009-05-15
:D Hello again. I am trying to completely wipe drive C on my HP using the Department of Defense default (three wipes using the 0's and 1's). Said drive houses my Windows installation. Anyone know how to do this with Ubuntu 9.04? :D

---

### Post by Therion on 2009-05-15
The only thing an install CD will have is a formatting utility.

Use DBAN if you really want to absolutely, totally, nuke the drive from orbit.

[http://www.dban.org/about](http://www.dban.org/about)

---

### Post by itnet7 on 2009-05-15
I would suggest you try shred, More about shred can be found here: [Shred examples]("http://www.fsckin.com/2008/01/09/using-shred-to-wipe-hard-drives-dod-uses-it-you-should-too/")

This is what I'm going to try next time I have a need!

Chris C. 
itnet7

---

### Post by aliencure on 2009-05-16
Thank you all for your responses. Tried Dban with no success. I went to the Shred example page but it is EXTREMELY confusing to me. I watched the video but it told me little next to nothing on how to select a drive to wipe. I really would not know what to do. If someone can give me a step-by-step basis to work with I might be able to pull it off. Thank you all for any help you can give me.

---

### Post by itnet7 on 2009-05-17
I will try and see if I can document the use of shred here for you... to overwrite the c partition.

Thanks,

Chris C.
itnet7

---

### Post by aliencure on 2009-05-18
Here is what came up in terminal when I tried using shred commands:

derek@derek-desktop:~$ shred -f -n 3 -u -v -x -z hp
shred: hp: failed to open for writing: No such file or directory
derek@derek-desktop:~$ 

I used "hp" because that is how it is listed under the "places" menu. Though I found pages making shred less confusing, apparently I am still unsure how to locate the drive to be shredded. Any suggestions?

---

### Post by stefangr1 on 2009-05-18
shred -vfz -n 1 <partition>

The partition you wan't to erease has a name like /dev/sda or /dev/hda.
If you don't know the name of your partition you can look it up with the command "sudo fdisk -l"

Only one single overwrite will do. After that, at very high expenses (team of experts with fully equipped lab, electron microscope etc.) is needed to recover (if they're lucky) tiny fragments of data...

---

### Post by aliencure on 2009-05-18
This time I performed command and the end result:

derek@derek-desktop:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x217df2e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89741   720844551    7  HPFS/NTFS
/dev/sda2           89742       91201    11727450    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba41ba41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       58600   470704468+  83  Linux
/dev/sdb2           58601       60801    17679532+   5  Extended
/dev/sdb5           58601       60801    17679501   82  Linux swap / Solaris
derek@derek-desktop:~$ shred -vfz -n 3 /dev/sda1
shred: /dev/sda1: failed to open for writing: Operation not permitted
derek@derek-desktop:~$ 

Downloaded dban and tried again with a disk image but it still did not work.

---

### Post by itnet7 on 2009-05-18
> **aliencure said:**
> This time I performed command and the end result:

derek@derek-desktop:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x217df2e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89741   720844551    7  HPFS/NTFS
/dev/sda2           89742       91201    11727450    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba41ba41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       58600   470704468+  83  Linux
/dev/sdb2           58601       60801    17679532+   5  Extended
/dev/sdb5           58601       60801    17679501   82  Linux swap / Solaris
derek@derek-desktop:~$ shred -vfz -n 3 /dev/sda1
shred: /dev/sda1: failed to open for writing: Operation not permitted
derek@derek-desktop:~$ 

Downloaded dban and tried again with a disk image but it still did not work.

You would have to run the command with root privileges:

```
sudo shred -vfz -n 3 /dev/sda1
```

Try that and let us know if it works for you!

Chris C.
itnet7

---

### Post by aliencure on 2009-05-20
:KSDOH! Why didn't I think to try typing Sudo before the shred command? Thank you guys. Problem has been solved.:KS

---

### Post by XubuRoxMySox on 2009-05-22
LOL, I know... Sudo is like *Simon Says!*

[COLOR="Purple"]"Clean."[/COLOR]
"No."
[COLOR="Purple"]"**Sudo** clean."[/COLOR]
"Yes ma'am, right away!"

-Robin

---

