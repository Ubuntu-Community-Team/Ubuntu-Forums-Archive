---
title: "deleting my windows partiton - how will this affect grub/bootup?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by bionnaki on 2005-10-26
I am now 100% linux.
I'd like to delete my windows partition and format it as ext3
and use it to store my [backup](http://ubuntuforums.org/showthread.php?t=81311)
I have zero need for window anymore
and could use the space to backup my OS.

how will this affect grub? what should I do?

also, is ext3 a decent choice for filesystem?
the only thing on the partition will be a 20 gig
or so .bz2 backup of my ubuntu OS...

---

### Post by bionnaki on 2005-10-26
hmm
I think I'll do a fresh install
I'd rather not mess around
with the partition/boot tables
and have improper harddrive configurations
in my backup.

but the question still stands...
is ext3 a decent filesystem for
large storage?

---

### Post by Jenda on 2005-10-26
CONGRATULATIONS!!!
I love this!
```
sudo gedit /boot/grub/menu.lst
```
Find your Windows entry and delete it. I recommend making a few backup copies of the file and deleting the entry in each one. For added pleasure. Enjoy the formatting - I know I did!

---

### Post by Jenda on 2005-10-26
[QUOTE=bionnaki]hmm
I think I'll do a fresh install
I'd rather not mess around
with the partition/boot tables
and have improper harddrive configurations
in my backup.

but the question still stands...
is ext3 a decent filesystem for
large storage?[/QUOTE]
Not necessary. All you need to do is format the partition with ext3. It's a great fs, AFAIK.

---

### Post by bionnaki on 2005-10-26
thanks!

---

