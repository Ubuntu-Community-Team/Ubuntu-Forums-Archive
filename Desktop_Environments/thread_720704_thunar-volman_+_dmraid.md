---
title: "thunar-volman + dmraid"
date: 2008-03-10
forum: Desktop Environments
---

### Post by gegefr on 2008-03-10
Hi

I'm running Xubuntu, and I don't know if
thunar-volman is able to do what I'd like it to do:

I'm running xubuntu on a "fake" raid  0. Meaning I'm using dmraid and
my "usable" devices are in /dev/mapper/*, and i've got two
"non-usable" devices /sda and /sdb.

One of the problems is that thunar-volman shows me the "device"
/dev/sda1 while I'd like it not to since it is not a valid partition.
Is there a way to make it ignore it ?

The other "problem" is that I'd like thunar-volman to handle all my
partitions (/dev/mapper/*) the if they were removable devices, in
order to have "proper" shortcuts in thunar, places, desktop... (And
not having to mount them via fstab and then make symbolic links
everywhere...) In short, having the same behaviour than
gnome-volume-manager had.

I don't know if thunar-volman is supposed to work that way or not :s

If anybody knows how to do this or has a hint, you're welcome !

This is the only thing I miss from gnome ;)

Thanks in advance ! !

---

### Post by gegefr on 2008-03-11
nobody for this ? ;)

(up)

---

