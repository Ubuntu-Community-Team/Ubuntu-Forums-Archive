---
title: "creating a ubuntu live usb flash disk"
date: 2009-02-14
forum: General Help
---

### Post by test006 on 2009-02-14
Hi,
I am using the ubuntu 8.10 live CD to create a usb bootable flash disk.
When i use the usb disk to boot from i get following error message:
```
Could not find kernel image: linux
```
Can someone tell me whats wrong and is there any steps i have missed. I used the tool that comes with ubuntu to create the live usb flash disk. I have tried this on two PCs and i get same error message. Both PCs support booting from usb disk. 

Please advise how can i fix this problem.

Thanks

---

### Post by johnjohn2 on 2009-02-14
try doing it again, or just download another image and give that a go.

Regards John

---

### Post by test006 on 2009-02-14
> **johnjohn2 said:**
> try doing it again, or just download another image and give that a go.

Regards John
Hi,
I have done so many times that i pretty much lost count of it now. I gave downloaded image many times and also used different PCs to create the live usb flash disk and still no luck. I have tried many other tools as well and no luck with them so i thought lets create ubuntu live usb flash disk using ubuntu tool....but still no luck...I have also used fedora image and backtrack3 image and no luck...

Only thing i get is the error message as per my first post and a boot prompt.

Thanks

---

### Post by johnjohn2 on 2009-02-14
> **test006 said:**
> Hi,
I have done so many times that i pretty much lost count of it now. I gave downloaded image many times and also used different PCs to create the live usb flash disk and still no luck. I have tried many other tools as well and no luck with them so i thought lets create ubuntu live usb flash disk using ubuntu tool....but still no luck...I have also used fedora image and backtrack3 image and no luck...

Only thing i get is the error message as per my first post and a boot prompt.

Thanks

well i think there is your problem, are u using ubuntu to burn the image to the disk? Cause if so that may be the cause of you problems.

You could try mounting the image file (.iso) and copy all of the files to you reformatted thumbdrive and try that.

Have you posted on the relevant distros forum regarding this?

---

### Post by test006 on 2009-02-14
> **johnjohn2 said:**
> well i think there is your problem, are u using ubuntu to burn the image to the disk? Cause if so that may be the cause of you problems.

You could try mounting the image file (.iso) and copy all of the files to you reformatted thumbdrive and try that.

Have you posted on the relevant distros forum regarding this?
Hi,
I just did as per suggestion. On my windows PC i used daemon tools to extract thw ubuntu iso image to my usb flash disk. When i tried booting the PC using the flash disk i get following error message:
```
Remove disks or other media
Press any key to restart

```
I think this has something to do with making sure that usb disk in bootable and just copying the files across does not make it bootable. This is the reason i used the ubuntu tool, which i believe makes the usb flash disk to be bootable....but no luck...I thought this is pretty simple stuff but its turning out to be a long process.....

Thanks

---

### Post by johnjohn2 on 2009-02-14
Try searching google for > pendrive linux 

That may yield better results as i have had no issues with this but i don't use windows.

---

### Post by linux_tech on 2009-02-14
How to fix Could not find kernel image: linux error:
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)

---

### Post by test006 on 2009-02-15
> **linux_tech said:**
> How to fix Could not find kernel image: linux error:
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)
Hi,
I had a look at the url and than had a look at the syslinux.cfg.
Now in my case the syslinux file exists in the root directory and contents of the syslinux.cfg  file is as follows:
```

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

```
The menu.cfg and vesamenu.c32 file exists inside the /syslinux directory. Now inside the syslinux directory is also a syslinux.cfg file that is exactly the same as above.

Now looking at the pendrivelinux url. One of the points states that to fix this problem you do as follows:
```

If the syslinux.cfg file does exist and your still encountering the error, open the syslinux.cfg file with a text 
editor and make sure that the paths to your kernel and initrd files are correct.

```
In my syslinux.cfg file there is no reference to kernel or initrd files so how can i correct this....

This usb live flash disk was created using the ubuntu tool.

Please advise what should i do to fix this problem.....

---

### Post by adult swim on 2009-02-15
i have had success with the ubuntu tool and i have had it fail many ways.  i suggest using unetbootin, [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/), if you still have the iso on your computer, just point unetbootin to it and then to your usb drive and youll be set.  it usually only takes a few minutes.

---

### Post by test006 on 2009-02-15
> **adult swim said:**
> i have had success with the ubuntu tool and i have had it fail many ways.  i suggest using unetbootin, [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/), if you still have the iso on your computer, just point unetbootin to it and then to your usb drive and youll be set.  it usually only takes a few minutes.
Hi,
I used the unetbootin tool to create the live usb flash disk i an still get the following error message:
```

Could not find kernel image: linux

```

Here is the copy of the syslinux.cfg file thats on the root directory when i used the unetbootin tool:
```

default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

```
I have also attached the root level screen capture of the usb flash disk.
Please advise what if there is something is wrong and that i need to correct anything.

Thanks



Anyone any ideas how i can solve this issue.....

---

### Post by old_codger on 2009-02-20
I managed to get it to work, (albeit without 'persistence'), by formatting the USB stick to fat16 instead of fat32. I'm still experimenting atm.

---

