---
title: "Image mounting tool (like daemon tools)"
date: 2008-05-15
forum: Gaming &amp; Leisure
---

### Post by bravemenrun333 on 2008-05-15
...for ubuntu 8.04 hardy. anything around? thanks

---

### Post by Ameneon on 2008-05-15
gkmount lets you mount iso images like daemon tools or alcohol or whatever, and works perfectly fine. There are certain other formats it does not support but those can generally be converted and will work fine.

---

### Post by Thirsty Ferret on 2008-05-15
I use gmount-iso for mounting ISO images. Works effectively for my needs :)
[https://launchpad.net/gmount-iso](https://launchpad.net/gmount-iso)

---

### Post by bravemenrun333 on 2008-05-15
thanks, is there any way to mount also *.img files with gmount-iso?

---

### Post by sisco311 on 2008-05-15
[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

convert the file with ccd2iso:
```
sudo aptitude install ccd2iso
``````
ccd2iso filename.img filename.iso
``````
mkdir image-dir
sudo mount filename.iso ./image-dir -o loop
```The first command will install ccd2iso. The second will convert a file to iso. The last two will create a directory and mount the converted iso.(replace filename.img with the full path to the file)

---

### Post by ruha on 2008-05-15
you can also install acetoneiso for linux, it works good for the most sorts of images. You can download it from here [http://linux.softpedia.com/get/Multimedia/Audio/AcetoneISO-16724.shtml]("http://linux.softpedia.com/get/Multimedia/Audio/AcetoneISO-16724.shtml"). Open the readme for the install instructions.

---

### Post by bravemenrun333 on 2008-05-15
how do i install it? ive downloaded it to desktop, but somehow dont get it to install...
edit: im complete ubuntu/linux newbie

---

### Post by Melhisedek on 2008-05-15
exactly what I wondered as well :) Thanks guys!

---

### Post by Grishka on 2008-05-15
man, get AcetoneISO2 from getdeb: [http://getdeb.net/search.php?keywords=acetoneiso](http://getdeb.net/search.php?keywords=acetoneiso). that's easier than installing by hand.

---

### Post by bravemenrun333 on 2008-05-20
thanks for the getdeb link, installed very well.
but acetoneiso doesnt seems to be able to open images on external usb harddisks! i can browse only on the internal harddisk, cannot find the external harddisk when browsing to the image i want to open! how come?

---

### Post by sisco311 on 2008-05-20
Usually the external disk is [mounted]("https://help.ubuntu.com/community/Mount") in the /media directory of the filesystem (/media/disk or /media/disk-1).

---

### Post by Rohen on 2008-05-20
Thanks for the info exactly what I was looking for.

---

### Post by PatronSaint on 2008-06-28
I have a folder that I'm trying to turn into an ISO. It's Madden 08, and I'm trying to take it off my harddrive and onto a DVD as an ISO. I've installed AcetoneISO2, but it acts like it doesn't see anything? 

I'm new to Ubuntu so I'm sorry, I really can't figure some of these things out yet. Can anyone help me?

Thanks

---

### Post by cor2y on 2008-06-28
Instead of programs you can just use the nautilus based script for mounting ISO files.
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)
Its what i have been using since about 5.10 , it came with automatix as well but since thats no longer being worked on for ubuntu, the how to link should work just as well.

---

### Post by bulletxt on 2008-06-28
> **PatronSaint said:**
> I have a folder that I'm trying to turn into an ISO. It's Madden 08, and I'm trying to take it off my harddrive and onto a DVD as an ISO. I've installed AcetoneISO2, but it acts like it doesn't see anything? 

I'm new to Ubuntu so I'm sorry, I really can't figure some of these things out yet. Can anyone help me?

Thanks

you're probably selecting a folder which is a link. That won't work as it doesn't follow symbolic links. be sure you're selecting the exact folder where the harddrive is mounted, something like "/media/usbdrive". If it still does the same thing, copy the Madden folder to your home or desktop and then select that one.

---

### Post by xwang on 2008-08-17
I've installed the last acetoneiso package (2.0.2) on my Kubuntu 8.04.1, but when I mount an image, it mount it in /home/username/virtual-drives/1 as root:root instead of username:username.
Is it a acetoneiso problem or should I change some configuration in fuse or whatelse?
Thank you,
Xwang

---

