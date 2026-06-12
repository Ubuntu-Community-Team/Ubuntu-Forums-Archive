---
title: "Mounting ntfs drives"
date: 2005-04-11
forum: Desktop Environments
---

### Post by noxlord on 2005-04-11
Hello, I use Kubuntu for AMD64. I can't mount my ntfs drive, wich is kid of anoying... The error message say : hd1 not found in /etc/fstab or /etc/mtab. What line do I have to ad to mount my drive ?
Will I be able to write to ntfs to ?

---

### Post by Fab on 2005-04-11
yes, you can write to ntfs drives using captive
afaik its not recommended to use the normal ntfs driver to write to ntfs drives..
and i think your error is that it should be hdX1 where x is either a b c or whatever
a for the first harddisk
so i guess its hda1 for you ;)

regards

---

### Post by F for Fragging on 2005-04-11
[QUOTE=noxlord]Hello, I use Kubuntu for AMD64. I can't mount my ntfs drive, wich is kid of anoying... The error message say : hd1 not found in /etc/fstab or /etc/mtab. What line do I have to ad to mount my drive ?
Will I be able to write to ntfs to ?[/QUOTE]
 [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by dermotti on 2005-04-11
I followed the guide and it worked perfect.

---

### Post by noxlord on 2005-04-11
[QUOTE=F for Fragging][http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)[/QUOTE]

cool, i can at least read my files.. now, how do I use captive, or whatever app for writing to my ntfs drive ?

---

### Post by devil28 on 2005-04-11
you ca follow this thread: [http://www.ubuntuforums.org/showthread.php?t=10175](http://www.ubuntuforums.org/showthread.php?t=10175)

---

