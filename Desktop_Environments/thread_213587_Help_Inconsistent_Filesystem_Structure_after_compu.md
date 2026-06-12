---
title: "Help: Inconsistent Filesystem Structure after computer hung"
date: 2006-07-11
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-07-11
I was going about my business and my computer totally hung. Not sure why. Had to force reboot. please don't hit me :p 

Anyway now when I boot normally I get 

Error 16: Inconsistent Filesystem Structure

I can get into recovery mode like I am now. How can I fix this. I read to use fsck but don't know how. I ran it as root and it said the hdd was mounted and couldn't be checked.

Really need help 

Thanks

Ironfistchamp

---

### Post by Paerez on 2006-07-11
just pop in your ubuntu disk and boot it live, then run "sudo fsck" on the drive. In live mode the disk won't be mounted, and if it is, you can unmount it.

---

### Post by ironfistchamp on 2006-07-11
Thanks will that repair it?

---

### Post by Paerez on 2006-07-11
it will let you run fsck, which hopefully will repair it. The goal was to get fsck going to scan the drive (its like ScanDisk in Winxor$).

---

### Post by ironfistchamp on 2006-07-11
Cool it is running now. I wonder what it will return.

---

### Post by cptnapalm on 2006-07-11
Having been recently bitten by a filesystem error due to needing to hard reboot (X lock ups, I think, is the weakest link in the Linux chain), I am in sympathy with you.

The advice of Paerez will almost certainly work.

One thing I remember Debian doing ages ago was to automatically do a filesystem check, if the partition had problems, on boot up.  Probably created a ramdisk or something.  Things would be much nicer if Ubuntu would do something like that.  Most filesystem errors can be fixed very easily, so it isn't like it should be overly complicated.

---

### Post by Paerez on 2006-07-11
ubuntu checks the root partition every 30 boots if it is ext3, but I am not sure if it remembers having problems. The whole, "you cant run fsck on a mounted drive and you can't unmount the drive because thats where fsck is" is a funny conundrum, but thats why the ubuntu cd is also a live disc. Smart move!

---

### Post by cptnapalm on 2006-07-11
It still seems kind of stupid to need to have a CD to check a filesystem.  Hell, Windows even can do such checks and Windows is on my bottom of the barrel list.

I am pretty close to absolutely certain that when the OS attempts to mount a filesystem, it can tell whether or not it was unmounted properly.  I would see this not infrequently on my old Debian (unstable) machine.  And I'm mostly sure that it gotten taken care of during the next boot up cycle.

The Debian thing I remember wasn't what you mentioned; I was definitely using xfs and it did the check on its own, saving me all kinds of hassle.  Xfs takes all of a a few seconds to check.  I'm still of the opinion that upon encountering a filesystem start up problem, the OS ought to do at least a basic check and fix (fsck -p?).

Requiring a user to have a Live CD with them at all times in case of a kernel panic (which I have yet to encounter with stock Ubuntu kernels) or X lock up (which, even after these years still happens far too frequently) or any other situation where the drive does not unmount properly is a Bad Thing.

---

### Post by ironfistchamp on 2006-07-11
Interesting replies. Thanks people :) . I ran reiserfsck and it returned with no problems. Booted normally and presto it worked. This OS is crazee. Most are actually. Maybe it is me. It doesn't matter what I use but things spontaneously stop working. 

Oh well all is working now so I'm happy. There are some things in Linux that I think "Why can'tit do that... even windows can do that!"

Funny I can't think of any right now. Odd.

Thanks again

Ironfistchamp

---

### Post by mikelinux on 2006-11-11
Guys,
I have the same problem. Please help me if you can.
Suddenly my laptop stopped working (crashed). I rebooted and it says: "inconsistent filesystem structure".
Now following your suggestion I burned a cd with ubuntu linux (6.10) and I can run it.
But giving the command:
$ sudo fsck /dev/hda
fails, saying:

couldn't find ext2 superblock, trying backup blocks.
fsck.ext2: Bad magic number in superblock while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2 filesystem.
If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or
something else), then the superblock is corrupted, and you may trying running e2fsck
with an alternate superblock:
e2fsck -b 8193 <device>

I didn't run e2fsck since I don't know what it does and if it could hart.
Note, I'm not sure about /dev/hda but if I list them I get:
/dev/hda, /dev/hda1, /dev/hda2 as disks.

What should I do?
I am really worried.... I am afraid to had lost all data....
Can anyone suggest anything please?

Mik

---

### Post by Paerez on 2006-11-11
instead of doing hda, you should pick the ubuntu partition on hda. So try:
```
$ sudo fsck /dev/hda1
```

If you don't know which partition it is, open System->Administration->Gnome Partition Editor, and look for the big ubuntu one.

---

### Post by mikelinux on 2006-11-12
Hi again,

the problem looks to be much more serious.
Now I can't run ubuntu neither from the CD!
On the attempt of loading it I get these errors:

```
piix4_smbus 0000:00:07.3: IBM Laptop detected: this module may corrupt your serial EEPROM!
Refusing to load module!

```
And then a series of these errors:
```
Buffer I/O error on device hda, logical block <number>

```
Then:
```
mount function not implemented
run fsck
Buffer I/O error on device hda, logical block <number>

```
And then the screen clears up and nothing is shown and the loading freeze.

I am afraid my HD is broken. I hope there is a way to recover my data... maybe paying some professional service (which I don't know about). Thanks for any attempt of help.

Despaired,
Mik

---

### Post by mikelinux on 2006-11-12
Update.
I could load again the system from live cd.
I run:
```
$ fsck /dev/hda1
/:recovery journal
/:clean 217287/9682944 files 11773078/19350284 blocks

```
I then restart the laptop and mount manually the HD:
```
$ sudo mount /dev/hda1 myDisk
```
Now I can back up and save many things...
but it looks like many files are corrupted and not readable: I/O error.
Any idea how to fix this?

I guess my HD is broken and I should replace it... still would be nice to save the most.

Thanks to all.
Mik

---

### Post by Paerez on 2006-11-13
You seem to have fixed as much as you can. I would avoid use of that hard drive. Only use it when you have to back things up. The more you use it, the more stuff will be corrupted.

I am not experienced in hard disk failure and backup, hopefully someone else can help. If the data is extremely important, there are places you can bring your hard disk and pay them to recover it, because they will use their hardware to read your disk, even if the disk is dead.

---

### Post by mikelinux on 2006-11-13
Thank you all guys.

Paerez: I think you are right about the fact that I recovered the most I could. I am trying with dd_rescue but it looks like few of the files I wasn't able to get before are actually recoverable.
([http://ubuntuforums.org/showthread.php?p=1750920#post1750920](http://ubuntuforums.org/showthread.php?p=1750920#post1750920))

And again, yes, I will throw that drive away as soon as I've done.

Cheers, thanks again,
Mik

---

### Post by SickNick on 2007-06-05
I am using Ubuntu Studio and I baisically got the same problem. My computer froze and then i restarted to error 16 inconsistent filesystem structure. I popped in my Ubuntu Studio CD and went to rescue system, i was then asked to check which one my root user directory was and i chose dev/sdb2 which was the only one that didnt give me an error when choosing it. I then was asked wat to do and had the option of running a command from that filesystem. I ran sudo fsck it asked me if im sure i hit y and it automatically filled in yes... then it froze, i repeated after a few restarts for the same result. Then i tried fsck, fsck dev/hda1, fsck dev/sdb1, which all gave me the superblock error that was posted before. I have two scsi hard disks one has vista the other has ubuntu studio, vista starts fine, the weird thing, sometimes ill get error 16, another time it booted once, then froze, nd a few times it froze while trying to boot up, and a couple time i just got a grub command line, i also got error 18 once, nd then restarted nd got error 16, is my linux haunted lol

---

### Post by deadpickle on 2007-06-14
I have been having trouble with this. I ran the live cd and started ubuntu. then went to terminal and ran "sudo fsck /dev/hda". and recieved this error:
The superblock could not be read....

and it suggests that I use another superblock:
sudo e2fsck -b 8193 /dev/hda
Tried it and it did the same thing.
What do I do???

---

### Post by Paerez on 2007-06-17
"/dev/hda" is the whole drive. "/dev/hda#" is a partition. You want to run fsck on a partition.

You can type:
"fdisk -l" to see a list of all your partitions. Then pick one to check, and type (for example):

fsck /dev/hda1

---

### Post by hhan on 2008-06-04
Had the same problem with inconsistent filesystem but fsck turned out ok (ubuntu seems to have switched from hd* to sd* for my ide disks). The solution for me was using the ubuntu live cd, mounting the drive and reverting to the backup file for /boot/initrd.img-2.6.22-14-generic

---

