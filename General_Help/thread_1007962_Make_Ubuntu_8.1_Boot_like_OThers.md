---
title: "Make Ubuntu 8.1 Boot like OThers"
date: 2008-12-10
forum: General Help
---

### Post by eweb100 on 2008-12-10
I felt great pleasure while watching fedora boot because of all the code checking n stuff.. Is there a way i can make it look like other oses? and no the normal loading screen?

---

### Post by adult swim on 2008-12-11
go to a terminal and enter in ```
cp /boot/grub/menu.lst /boot/grub/menu.backup
``` then enter in ```
gksudo gedit /boot/grub/menu.lst
```  scroll to the bottom and you will see the choices that you are able to choose from in grub.  now you need to go to the kernel line of the kernel that you boot, most likely the top one.  it will look different, but similar to ```
title		Ubuntu 8.10, kernel 2.6.27-8-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot


```  do you see in the line that says kernel where it has quiet splash at the end?  erase off quiet splash and then save and close the file.  now when you start up you will see whats going on behind the scene.

---

### Post by eweb100 on 2008-12-11
Thanks

---

### Post by jpkotta on 2008-12-11
You should also change the defoptions in menu.lst.  That way when you update your kernel the changes will stick (menu.lst is updated when you update the kernel).
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

```

---

