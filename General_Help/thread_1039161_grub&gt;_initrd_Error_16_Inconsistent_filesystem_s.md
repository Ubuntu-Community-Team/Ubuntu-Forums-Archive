---
title: "grub&gt; initrd: Error 16: Inconsistent filesystem structure"
date: 2009-01-14
forum: General Help
---

### Post by mgol on 2009-01-14
My system works ok but I wonder what should I do if I got an error connected to initrd ramdisk. The usual setup of GRUB bootloader looks like that:
```
$ sudo grub
> root (hdX,Y)
> setup (hd0)
```
However, full configuration can sometimes require to specify kernel and initrd paths:
```
$ sudo grub
> root (hdX,Y)
> kernel /vmlinuz-2.6.*
> initrd /initrd-2.6.*
> setup (hd0)
```
However, initrd *always* returns an error:
```
> initrd /initrd-2.6.*
Error 16: Inconsistent filesystem structure
```

The question is - why is that and how to setup it correctly? I could believe that sth is wrong with my initrd images, but system boots correctly, so this should not be it...

---

### Post by caljohnsmith on 2009-01-14
When you use the Grub command line in linux to reinstall Grub to the MBR using the "root" and "setup" commands, you don't need to specify a kernel or an initrd image. Those are only used by Grub on start up when you actually want to boot Ubuntu. From what I can tell, you will always get an "error 16" if you specify the kernel and initrd image while in the Grub CLI in linux. :)

---

### Post by mgol on 2009-01-14
OK, now I understand. So I wouldn't probably recieve this error if I entered grub by pressing 'e' when GRUB menu is displayed and used this command then, am I right? :)

---

### Post by caljohnsmith on 2009-01-14
> **mgol said:**
> OK, now I understand. So I wouldn't probably recieve this error if I entered grub by pressing 'e' when GRUB menu is displayed and used this command then, am I right? :)
Do you mean pressing "c" on start up to get the Grub command line? If so, I think you're right, you wouldn't receive the same error (although I haven't checked to make sure). :)

---

### Post by mgol on 2009-01-14
Yes, I meant 'c', my mistake. Thanks for info. :)

---

