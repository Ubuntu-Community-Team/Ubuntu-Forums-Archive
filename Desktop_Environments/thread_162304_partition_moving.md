---
title: "partition moving"
date: 2006-04-18
forum: Desktop Environments
---

### Post by willhurt on 2006-04-18
hi,

i have two 2partitions on my hdd one for windows and one for linux oh yeh and the linux swap. the trouble is they are a bit jumbled up:

70gb hdd:

30gb windows
7gb empty
15gb ubuntu
17gb empty
1gb swap

i want to push the ubuntu partition up next to the windows one and then make a large fat32 partition for my music which both can share;

so afterward my hdd would read

30gb windows
15gb ubuntu
25gb shared fat32
1gb swap
is this possible without messing up ubuntu. by using partition magic[windows] i can get the sector and cylinder heads for the positions of the newly moved partitions, is there a way of entering this into grub so my ubuntu partition doesnt mess up and everything works hunky-dory?? Would i have to do this in ubuntu then go to windows and resize or resize in ubuntu- i dont know of any linux partition managers?

if you can help that would be great!!!!

---

### Post by outofnicks on 2006-04-19
The partition manager program "parted" is on the Ubuntu install CD, it's a command-line app but easy to use. This post:

[http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960)

tells how to use parted to resize partitions, I send you there as it tells how to access parted on the CD. Then go to the parted User Manual at:

[http://www.gnu.org/software/parted/manual/html_mono/parted.html](http://www.gnu.org/software/parted/manual/html_mono/parted.html)

which will tell you how to move partitions.

---

### Post by wylfing on 2006-04-19
I think gparted is a lot easier to work with than parted itself. Do this:
```
sudo apt-get install gparted
```
and then this:
```
sudo gparted
```

---

### Post by outofnicks on 2006-04-20
Can you edit a booted partition with that? That's why I recommended the CD, thought you couldn't. 
Gparted may be on the live CD, perhaps?

---

### Post by willhurt on 2006-04-20
ok,
just to make sure ive got this right!

so its best to use a gparted or parted from inside linux or from the livecd/installation cd rather than using partitionmagic in windows/

if i use gparted/parted will that update grub as to where the ubuntu partition begins ends- so that i dont loose everything. or do i have to do that myself later - if so how do i go about this, cheers

will [ and thanks for the replies]

edit- after scanning parteds user manual it says something to do with LBA, am i on th eright track there?

---

### Post by wylfing on 2006-04-20
Hm, not sure I understand your post. The caution from **outofnicks** is proper -- you should do some kind of alternate booting so that you aren't messing around with the partitions on the same disk that you're booted from. The live CD is a good option, and gparted is definitely on there.

You don't need to worry about GRUB.

It also seems like you are worried about data loss, and you should be. It is never 100% safe to tinker with partitions. You should always back up critical data before doing any partition adjustments. There is a good chance everything will be fine, but you never know.

---

### Post by willhurt on 2006-04-20
thanks wylfing and outofnicks, ill go ahead and move the partition once ive downloaded the live-cd. your help has been invaluable and hopefully will save me having to reinstall[and configure!] ubuntu which i didn't find too easy.

ill definately makes sure i backup my files both in windows and ubuntu.

wylfing -- i had presumed that grub booted into ubuntu by looking for the partition ubuntu was installed on, and i thought it knew where this partition was just from a couple of numbers detailing where the cylinders begin and end for that partition. 

[hypothetical i.e.] hd0,1 == start10,000 - end20,000

so i thought if i moved the ubuntu partition along the drive to 5,000 -15,000 grub would still think ubuntu was at 10,000-20,000 and hence not be able to boot up.

from what you're both saying thats not the case. thanks once again!!

---

