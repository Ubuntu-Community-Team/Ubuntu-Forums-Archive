---
title: "Hard disk failure"
date: 2006-01-17
forum: General Help
---

### Post by Janux on 2006-01-17
I have a problem with my hard disk. Yesterday the computer couldn't boot because the root was damaged and fsck can't repair it.

Now I'm running from the file CD, because now I have a problem with GRUB (Error 2)

If I run fsck from the command line with the live CD I get the following:
```
$ sudo fsck /dev/hda
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I want to recover my files and it would be great if someone can help me in this.

---

### Post by earobinson on 2006-01-17
Have your tried to mount the hd with the live cd? Then you could copy them to another hd or burn them.

---

### Post by Janux on 2006-01-17
[quote=earobinson]Have your tried to mount the hd with the live cd? Then you could copy them to another hd or burn them.[/quote]
Thanks for the quick response.
Yes, I tried:

```
$ sudo mount -t ext3 /dev/hda1 /media/files
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So, let's try that
```
$ dmesg | tail
[4295825.213000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[4295825.214000] EXT3-fs: group descriptors corrupted !
[4295838.232000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[4295838.233000] EXT3-fs: group descriptors corrupted !
[4295853.914000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295853.914000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295854.037000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295854.037000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295855.082000] EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[4295855.084000] EXT3-fs: group descriptors corrupted !
```

---

### Post by earobinson on 2006-01-17
this thread might help [http://www.ubuntuforums.org/showthread.php?t=110221&highlight=Hard+disk+failure](http://www.ubuntuforums.org/showthread.php?t=110221&highlight=Hard+disk+failure)

EDIT: looking into this more...

---

### Post by Janux on 2006-01-17
I read the thread but I'm afraid that I don't have Windows installed in this PC and most of these tools work under that OS. I tried with TestDisk ([http://www.cgsecurity.org/index.html?testdisk.html](http://www.cgsecurity.org/index.html?testdisk.html)) but that tool didn't list my damaged hard disk.

Oh, well, I might try to get another hard drive, install XP, boot from there and try to recover the data...

---

### Post by earobinson on 2006-01-17
Thats looking like your best bet sorry, My advice is to unplug the hd untill you are ready to try and restore it.

Let us know how it goes

Will post if I find anything new.

---

