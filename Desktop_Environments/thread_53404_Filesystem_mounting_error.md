---
title: "Filesystem mounting error"
date: 2005-07-31
forum: Desktop Environments
---

### Post by web250 on 2005-07-31
I just installed Kubuntu today outright, after dual booting for a while. I used to use ReiserFS, but was urged by many to use ext3...which is fine, i dont really care either way.

My partition table is as followed:
swap 1.2 gb
/ ext3 20gb
/home ext3 98gb

When Kubuntu first loads up, and I get the white text on black screen, it mounts / and /home

While /home is correctly identified as ext3, / is idnetified as ext2fs. However, KDE recognizes / as ext3. How can I make sure that / is indeed ext3, and if it isn't how can i convert?

---

### Post by cwaldbieser on 2005-07-31
```
$ mount
```
should tell you what file systems are currently mounted and how they are recognized.  I am not sure what programs you are using to get the two different views you mention.

As for conversion, I am a little unsure of all the intracacies required for backing up and restoring the root filesystem.  I don't know if there is an easier way to upgrade.

---

### Post by web250 on 2005-07-31
[QUOTE=cwaldbieser]```
$ mount
```
should tell you what file systems are currently mounted and how they are recognized.  I am not sure what programs you are using to get the two different views you mention.

As for conversion, I am a little unsure of all the intracacies required for backing up and restoring the root filesystem.  I don't know if there is an easier way to upgrade.[/QUOTE]

Ok

```
$ mount
``` 

gives tells me that / is mounted via ext3.

I used kinfocenter to get me one of the views...the other was read striahgt from the intial text output

```
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
``` 
is the exact output of mount.

---

### Post by cwaldbieser on 2005-07-31
Well it looks like ext3 to me.

It may be that the filesystem is mounted/unmounted/remounted for some reason.   If you do a

$ dmesg | grep ext

can you find any reference to the filesystem being remounted as ext3?  I probably wouldn't worry about it, myself.

---

### Post by web250 on 2005-07-31
[QUOTE=cwaldbieser]Well it looks like ext3 to me.

It may be that the filesystem is mounted/unmounted/remounted for some reason.   If you do a

$ dmesg | grep ext

can you find any reference to the filesystem being remounted as ext3?  I probably wouldn't worry about it, myself.[/QUOTE]

That gets me this:
```
Adding 1172704k swap on /dev/hda1.  Priority:-1 extents:1
``` 

EDIT:
doing $ dmesg | grep hda
it says (among other things):
```
EXT3 FS on hda2, internal journal
``` 
hda2 is my / partition.


What does that mean?

---

### Post by cwaldbieser on 2005-08-01
[QUOTE=web250]That gets me this:

doing $ dmesg | grep hda
it says (among other things):
```
EXT3 FS on hda2, internal journal
``` 
hda2 is my / partition.


What does that mean?[/QUOTE]

I believe it confirms that your root partition was mounted as ext3.  I am not sure what part of the boot process mounted it as ext2 (as I cannot watch your boot messages scroll by), but it appears to be a temporary condition.

---

