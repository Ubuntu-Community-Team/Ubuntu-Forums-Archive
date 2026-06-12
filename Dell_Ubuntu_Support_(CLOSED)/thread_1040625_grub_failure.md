---
title: "grub failure"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gourab17 on 2009-01-15
i have an xps1330
on which i installed both vista (home ) and ubuntu (8.04)....
initally everything works too good.....
but within 30 reboots the grub suddenly disappears ......
can anyone tell me the rational behind this and how to prevent it ??

---

### Post by 2hot6ft2 on 2009-01-15
> **gourab17 said:**
> i have an xps1330
on which i installed both vista (home ) and ubuntu (8.04)....
initally everything works too good.....
but within 30 reboots the grub suddenly disappears ......
can anyone tell me the rational behind this and how to prevent it ??
Since you don't say if it's a desktop or a laptop. And you don't say if you can still boot into either system. Boot the ubuntu livecd and do

Desktop...more than 1 drive
In a terminal use
Applications>Accessories>Terminal

```
sudo grub
find /boot/grub/stage1
```

This will return (hdX,Y), where X and Y are some numbers. Use these numbers below:

```
root (hdX,Y)
setup (hdX)
quit
```

If a laptop to restore Grub to your MBR, boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

As for why it happened I don't know.

---

### Post by gourab17 on 2009-01-15
its say "error 17 : can not mount selected partition "

---

### Post by gourab17 on 2009-01-16
mine is a laptop...........
is there any way out now ????

---

### Post by pmthien on 2009-01-16
Hi guy,
You should try these thing.
Boot your computer using live cd

sudo mount -o ro /media/ /sda1/
sudo mount -o /media/dev/ /dev/
sudo mount -0 /media/proc /proc/

after that
sudo chroot /media/

after that
grub
then,
grub> find /boot/grub/stage1
grub> root (hd0,1)
grub> setup (hd0)
grub> exit

finally, you should unmount your mount point using
sudo umount.

hope that help
thanks,
Thien

---

