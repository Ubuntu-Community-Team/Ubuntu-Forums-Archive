---
title: "Hard disk partition shown on desktop"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by lastkey on 2007-05-31
My vfat partitions are shown on desktop, i want to hide them. I unchecked the volume visible key in configuration editor but it's only hiding the same partitions with Names as set in windows but now it is showing partitions as 7GB FAT32 Volume (hdb10)

---

### Post by vnfatpig on 2007-06-12
I had the same problem. Do you have any method to solve that?

Thanks.

---

### Post by vanadium on 2007-06-12
Everything that is mounted in /media is shown as a desktop icon. Mount the media that you do not want to see on the desktop elsewhere, typically under /mnt.

---

### Post by Eddie Hung on 2007-06-14
> **vanadium said:**
> Everything that is mounted in /media is shown as a desktop icon. Mount the media that you do not want to see on the desktop elsewhere, typically under /mnt.

Are you sure that's true? I tried mounting my NTFS and FAT partition into /mnt/* and they were still present on my desktop when I ticked the gconf nautlius key...

Eddie

---

### Post by ykpaiha on 2007-06-14
in a terminal:
gconf-editor
then:
apps=>nautilus=>desktop
on the right window you can check or uncheck any option
trash, desktop, volume ....icon can be hidded or shown.
in your case just uncheck the volume visible option 
prety easy isn't it?

---

### Post by Eddie Hung on 2007-06-15
> **ykpaiha said:**
> in a terminal:
gconf-editor
then:
apps=>nautilus=>desktop
on the right window you can check or uncheck any option
trash, desktop, volume ....icon can be hidded or shown.
in your case just uncheck the volume visible option 
prety easy isn't it?

And that was the gconf nautlius key I was talking about. My specific problem is that I don't want my internal hard disk partitions to be shown on the desktop - but I do want any external devices (usb memory sticks, external drives) to be displayed, and mounting my internal disks inside /mnt/ does not seem to have any effect.

Eddie

---

### Post by samartha on 2008-05-27
> **Eddie Hung said:**
> And that was the gconf nautlius key I was talking about. My specific problem is that I don't want my internal hard disk partitions to be shown on the desktop - but I do want any external devices (usb memory sticks, external drives) to be displayed, and mounting my internal disks inside /mnt/ does not seem to have any effect.

Eddie

I have the same issue too ... 

Hope someone helps.

---

### Post by Jerubaal on 2008-06-17
Have you solved this to your satisfaction yet? If so, how?

---

### Post by caseyjones on 2008-06-17
I was able to solve it in Fedora 9. See this :
[https://bugzilla.redhat.com/show_bug.cgi?id=384201](https://bugzilla.redhat.com/show_bug.cgi?id=384201)

[FONT=monospace]I did exactly what was mentioned right below '[/FONT]
Description of problem:', rebooted and the problem was solved. When using a SD card or 
flash drive in one of the laptops slots, an icon appears on the Desktop just as usual.

HTH

---

