---
title: "hello all"
date: 2009-01-11
forum: General Help
---

### Post by sdolan921 on 2009-01-11
I am pretty sure i have an i/o or mount point issue.

shawn@shawn-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=b8d2475f-509e-48c4-a70b-db5e8f01f8fd  /              **ext3         relatime,errors=remount-ro  0  1**
# /dev/sda5
UUID=10079672-98ad-49eb-9c72-13f6a886c632  none           swap         sw                          0  0  
/dev/sda                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /media/sda1    ext3         defaults                    0  0  

My comp is very slow and i have an icon of/dev/sda1[PHP][/PHP] on my desktop
Im a real bootstap kind of guy, .....but this is killing me any help would be much appreciated!

---

### Post by Elfy on 2009-01-11
You've got /dev/sda1 mounting twice
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
> # [COLOR="Red"]/dev/sda1
UUID=b8d2475f-509e-48c4-a70b-db5e8f01f8fd [/COLOR]/ ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=10079672-98ad-49eb-9c72-13f6a886c632 none swap sw 0 0
/dev/sda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
[COLOR="Red"]/dev/sda1 /media/sda1 ext3 defaults 0 0 [/COLOR]

Why did you add it? Try commenting out the last line with a #.

---

### Post by schilcha on 2009-01-11
had the same in mind as forestpixie... never mind

> **sdolan921 said:**
> 
[...]
# /dev/**sda1**
UUID=b8d2475f-509e-48c4-a70b-db5e8f01f8fd  /              **ext3         relatime,errors=remount-ro  0  1**

[...]

/dev/**sda**                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/**sda1**                                  /media/sda1    ext3         defaults                    0  0  


It seems, you have sda1 twice in your fstab + sda itself additionally.

Try running the command "mount" to see which partitions are actually mounted where on your system.

---

