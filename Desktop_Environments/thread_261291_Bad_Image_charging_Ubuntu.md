---
title: "Bad Image charging Ubuntu"
date: 2006-09-20
forum: Desktop Environments
---

### Post by waffen on 2006-09-20
Hi,

In my Dell Latitude C640 this image: 

[http://shots.osdir.com/slideshows/original.php?release=659&slide=2]("http://shots.osdir.com/slideshows/original.php?release=659&slide=2")

appears in the left bottom square....

and the grub image shows very small, but centered...

any idea?? :confused: 

Thanks!!

---

### Post by it.henrik on 2006-09-20
press FN+F7 while you see these screens

---

### Post by waffen on 2006-09-20
> **it.henrik said:**
> press FN+F7 while you see these screens

Hi,

Thanks for the tip! but only function with the Grub image.

With the splashy image I need to make this:

```
$ sudo gedit /boot/grub/menu.lst
```

and add vga=791:

```
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash vga=791
```

and that code center the screen...

Thanks!

---

