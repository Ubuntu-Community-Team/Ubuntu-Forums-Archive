---
title: "Can get rid of Icons for improperly unmounted drives"
date: 2008-07-22
forum: Desktop Environments
---

### Post by Jcarr_toonist on 2008-07-22
I have Hardy running at my workplace where usb hard drives are being constantly plugged in and removed. On the few occasions where the drive is not properly unmounted the icon that is generated for that item remains on the desktop and cannot be removed unless I restart the X environment. I have noticed that Ipod icons do the same thing

Does anyone know of any way they can be removed?

---

### Post by Tim Sharitt on 2008-07-23
Running umount from the terminal works for me.
```
sudo umount /media/MYBOOK
```
(substitute your device name of course)

---

### Post by Gatemaze on 2008-07-23
I think (s)he means that the icons are left on the desktop when they are not even asked to be unmounted... they are just plugged out from the socket... i saw this issue yesterday when i tried to see what would happen if i did so... it doesn't always occur and it is a bad practice if they are unplugged before unmounted.

Have you tried to unmount it after it is unplugged? I don't think it will work, but you never know.

---

### Post by Duranxl on 2008-07-23
I have this problem too.
And the bad thing about it: My externa USB is mounted as let's say "disk"
Then when i turn it off, the "disk" remains on my desktop/my computer...so then when i turn it on again, ubuntu will mount it as "disk_"...causing all my shortcuts/download programs to fail because it can't find "disk".
Very annoying -.-

---

### Post by Jcarr_toonist on 2008-07-23
> **Gatemaze said:**
> I

Have you tried to unmount it after it is unplugged? I don't think it will work, but you never know.

Tried that but its returns a error message, can't recall what it is. I cannot delete the icon either. I know that it is bad practice for the mounted drive to be disconnected without being unmounted but unfortunately for what the machine is being used for it happen more then a few times a day and the desktop is becoming littered with icons for drives that are not mounted. 

Even if there was a way to stop ubuntu from automatically generating a icon whenever a drive is mounted that would be enough for me.

---

### Post by mcduck on 2008-07-24
" sudo umount -f /media/NAMEOFTHEDRIVE" should do the trick.

Of course it would be better to make sure that people unmount the drives correctly in the first place, if not only to get rid of the extra icons, but also to prevent data loss (and in worst case scenario file system corruption)..

The desktop icons can be disabled through Configuration Editor. Press Alt-F2 and run "gconf-editor", then browse to apps/nautilus/desktop. Different desktop icons (home, trash, compter, network and mounted drives) can be enabled & disabled there. However new directories will still be created in /media and the icons will still show under Computer, so you should still regularly use the "umount -f" command.

---

### Post by mcduck on 2008-07-24
> **Duranxl said:**
> I have this problem too.
And the bad thing about it: My externa USB is mounted as let's say "disk"
Then when i turn it off, the "disk" remains on my desktop/my computer...so then when i turn it on again, ubuntu will mount it as "disk_"...causing all my shortcuts/download programs to fail because it can't find "disk".
Very annoying -.-

You could configure the drive in /etc/fstab using it's UUID, or give the partition a label so it would always be mounted with the same name and in to the same place..

---

### Post by Duranxl on 2008-07-24
> **mcduck said:**
> You could configure the drive in /etc/fstab using it's UUID, or give the partition a label so it would always be mounted with the same name and in to the same place..

It does mount the same everytime, but it doesnt unmount when i turn it off...so when i turn it on, it's mount name is already in use

---

### Post by mcduck on 2008-07-24
> **Duranxl said:**
> It does mount the same everytime, but it doesnt unmount when i turn it off...so when i turn it on, it's mount name is already in use

You should unmount/eject it before turning it off, just like any other external media..

---

### Post by Jcarr_toonist on 2008-07-29
> **mcduck said:**
> " sudo umount -f /media/NAMEOFTHEDRIVE" should do the trick.



Thank you, that does the trick. Now comes the longer harder task of reminding everyone to unmount their drives when they are done.

---

### Post by mcduck on 2008-07-30
> **Jcarr_toonist said:**
> Thank you, that does the trick. Now comes the longer harder task of reminding everyone to unmount their drives when they are done.

If nothing else works, how about writing the instruction to the backgrounnd image? ;)

---

