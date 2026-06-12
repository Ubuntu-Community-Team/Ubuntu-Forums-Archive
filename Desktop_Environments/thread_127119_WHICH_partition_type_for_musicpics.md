---
title: "WHICH partition type for music/pics?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by joey111 on 2006-02-08
hi,
i am thinkingabout creating an own partition for music and pics,
bec. of two reasons: 
-i really want to have it undestructable
- i have ubuntu and am trying on another partition fedora (so it would be good if ic can just accessit without navigating for long)-
-i dont want to navigate for long through my homedirectory when i just  want get some music.

so what would u recommend as partition type ext3?REISER, EXT,EXT3 ETC ETC?
or is there something faster/ more stable (i know ext2 is more stable, isnt it), that can be accessed through fedora too?

do u have your music in home directory or in separate partition?
thx

---

### Post by olafura on 2006-02-09
Reiser is faster for lots of small files so I think it will be best for you.
XFS is faster for large files.
Both should be able to restored in case of a desaster, but I harddrives
can crash, two did in a space of a week with two diffrent computers
at home.

You should backup your file as a rule.


Olafur Arason

---

### Post by rado_london on 2006-02-09
Well I have that kind of partition formatted as EXT3 and I am very happy. It is fast enough for me. Also it does some checking every 30 mounts so it will recover any bad inodes etc.

---

### Post by alfonz on 2006-02-09
[QUOTE=rado_london]Well I have that kind of partition formatted as EXT3 and I am very happy. It is fast enough for me. Also it does some checking every 30 mounts so it will recover any bad inodes etc.[/QUOTE]

This is true, just happened to me on my last reboot and all was healthy :D

I normaly use ext3 for /   and reiserfs for /home because I make seperate partitions for /home directory

---

### Post by danhm on 2006-02-10
I do the same as alfonz, and it works great for me.

Just don't do something stupid like use FAT16.

---

### Post by dcstar on 2006-02-10
And use the "noatime" option in your/etc/fstab to improve disk efficiency.

---

### Post by rado_london on 2006-02-10
My option in /etc/fstab are defaults. How can I add that noatime?

---

### Post by dcstar on 2006-02-10
[QUOTE=rado_london]My option in /etc/fstab are defaults. How can I add that noatime?[/QUOTE]
My fstab entry for my root filesystem:

/dev/hda4       /               ext3    	defaults,noatime,errors=remount-ro	0       1

---

