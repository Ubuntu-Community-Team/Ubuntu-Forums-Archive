---
title: "DD Command Help"
date: 2009-06-10
forum: General Help
---

### Post by Waqsss on 2009-06-10
Hi guys,

I am trying to backup a few CD's I have on my ubuntu 9.04 with the following terminal command:


dd if=/dev/cdrom of=/image.iso


What I am trying to do is back them up directly to my USB drive because at present it goes on my internal hard drive. Can someone advise on what I need to put in the command?

Thanks

---

### Post by 1234 on 2009-06-10
the command is right but you need to specify the path to your USB

here on 
 dd if=/dev/cdrom of=/image.iso

you are writing the image on your root directory. you may try like of=/media/sda?/image.iso   sda?= your usb

---

### Post by Waqsss on 2009-06-10
according to Gparted the device path is /dev/sdd2

---

### Post by Waqsss on 2009-06-10
I tried the following commands which did not work:

dd if=/dev/cdrom of=/media/sdd2/image.iso

dd if=/dev/cdrom of=/dev/sdd2/image.iso

dd if=/dev/cdrom of=/mnt/sdd2/image.iso



All of them give me the error "dd: opening '/media/sdd2/image.iso': No such file or directory

---

### Post by Waqsss on 2009-06-10
Figured it out. I used "df -h" to see what was mounted and where it was mounted. The path was actually "/media/disk"

Thanks :)

---

### Post by andrew.46 on 2009-06-10
Hi Wasqss,

> **Waqsss said:**
> Figured it out. I used "df -h" to see what was mounted and where it was mounted. The path was actually "/media/disk

You could also use:

```
sudo fdisk -l
```

and I suspect this is the more conventional way?

Andrew

---

