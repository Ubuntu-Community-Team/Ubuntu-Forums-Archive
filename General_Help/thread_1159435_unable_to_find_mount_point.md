---
title: "unable to find mount point"
date: 2009-05-14
forum: General Help
---

### Post by hossein.koozehgar on 2009-05-14
Hi every one
I am new to ubuntu and i have installed it via Microsoft Windows. I did this since i wanted to become familiar more with ubuntu and then switch completely to it.

any way, I have a problem in gparted it gets me the error "unable to find mount point" and i dont know how to fix it.

i have checked other thread but they were not like my problem. here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

``` 

Would you please help me solve this problem

---

