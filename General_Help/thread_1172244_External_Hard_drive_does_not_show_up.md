---
title: "External Hard drive does not show up"
date: 2009-05-28
forum: General Help
---

### Post by Zaba5 on 2009-05-28
I just installed ubuntu 8.10 on my comp, and it works great. my usb drive works well, but whenever  i try to plug in my external hard drive (Western Digital MyBook) nothing happens. I installed NTFS-3g and still nothing. What is wrong?

---

### Post by Hansmc on 2009-05-28
Are you going through a powered usb hub? I have had trouble with them before. In fact I have never had one that works on Ubuntu. If it is a powered usb drive try plugging in the power then the usb cable, then try it the other way around. I have found it is picky about how things are done, but they always seem to work in the end. The command lsusb will list the usb devices that Ubuntu has found. Hope this helps.

---

### Post by Zaba5 on 2009-05-28
thanks, will try when i get back home.

---

### Post by drs305 on 2009-05-28
With the external device plugged in and powered, run:
```

sudo fdisk -l

```
This command will list all the devices the system currently sees.
You can also run this to see if the device is mounted somewhere you haven't yet looked:
```

mount | grep "/dev/sd"

```

You could also check this setting to make sure "automount" is enabled:
```
gconf-editor /apps/nautilus/preferences/media_automount
```

---

### Post by Zaba5 on 2009-05-28
i tried running fdisk already but it doesnt detect it. When i get back home ill first try Hansmc's idea, and then ill run ```
mount | grep "/dev/sd"
```
 
edit-
i already ran the nautilus and my automount is enabled

---

### Post by matey3 on 2009-05-28
seems to me it is a power problem.
I have a WD external HDD but it requires a power adapter (which I am sure you know) but I have a Toshiba external HDD which gets its power from USB ,

Do you get any light come on on your HDD?
Have you tried a different USB slot? (like the ones in the back of computer or if you have a laptop on the other side).
Has lspci show anything?

---

### Post by drs305 on 2009-05-28
> **Zaba5 said:**
> i tried running fdisk already but it doesnt detect it. When i get back home ill first try Hansmc's idea, and then ill run ```
mount | grep "/dev/sd"
```

If fdisk isn't detecting it then it won't show up as mounted either so the mount command won't provide any info on the drive.

Your system isn't recognizing the drive. Have you successfully run this drive elsewhere?

---

### Post by Zaba5 on 2009-05-28
yes, it worked perfectly fine on my Vista computer. I dont understand why nothing is happening

---

### Post by drs305 on 2009-05-28
> **Zaba5 said:**
> yes, it worked perfectly fine on my Vista computer. I dont understand why nothing is happening

This shouldn't be the problem since the drive isn't even found, but did you umount it normally the last time you used it in windows? Normal poweroff or use the "safely unmount" option. You could try mounting it again in windows and then use the "safely unmount" option to make sure the file structure is correct.

---

### Post by Zaba5 on 2009-05-28
> **Hansmc said:**
> Are you going through a powered usb hub? I have had trouble with them before. In fact I have never had one that works on Ubuntu. If it is a powered usb drive try plugging in the power then the usb cable, then try it the other way around. I have found it is picky about how things are done, but they always seem to work in the end. The command lsusb will list the usb devices that Ubuntu has found. Hope this helps.

just tried this

wow it works!! thanks for all your help guys:p

---

