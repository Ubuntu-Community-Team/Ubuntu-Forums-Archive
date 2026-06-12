---
title: "/media/usbdisk/ and sda1w"
date: 2006-07-05
forum: Desktop Environments
---

### Post by ubiwankanubi on 2006-07-05
when I plug in a usb drive, I can see the icon on the desktop, but if I click it, it tells me it can't mount sda1 because it's already mounted in /media/usbdisk/.
I can go to /media/usbdisk/ to see the files, but I can't right click the desktop icon to unmount it. I need to go to the file:/// and rightclick and unmount the disk from there.

Is there a way to fix this so I can click the desktop icon that appears when I plug in the usb drive to take me to the usb contents without giving me that warning, and so I can easily unmount from the desktop?

Also of note, when I do finally get to unmount the usb drive, the icon is still visible, but it seems I can remove the usb drive ok.

When using linux and usb pen drives, do you always need to mount/unmount? or can I just plug it and and pull it out whenever?

---

### Post by dpaint4 on 2006-07-05
I second every aspect of this question but especially whether or not mounting and unmouting is required.

---

### Post by ash211 on 2006-07-05
Mounting a usb drive makes it visible to the computer, so yes that part is required.  Unmounting is a little different, though.  

If you pull the drive out while data is being written to it, corruption can occur.  Unmounting basically just finishes writing all the data to the drive and then lets you know that you can pull the drive out safely.  Windows doesn't have an unmount option, so you can only hope it's done writing to the drive when you pull it out.  Waiting until flashing lights stop if your drive has them is all you can do in Windows.

So mounting is required, and unmounting is highly recommended.

---

### Post by ionophore on 2006-07-05
>Windows doesn't have an unmount option, so you can only
>hope it's done writing to the drive when you pull it out.

Not true, in Windows XP/2000 you can right click on a tray icon that appears when you plug in auto-detected storage devices and select "safely remove hardware."  This is the windows way of un-mounting things, they just don't call it "un mounting."

A little off topic, i know... I'll go away now :)

---

### Post by ash211 on 2006-07-06
Sorry, yes I forgot about that, I use Windows so little now!

---

### Post by ubiwankanubi on 2006-07-06
ok, so mount and unmount should be done, but how can I get the desktop icon that automatically appears to work right? when I click it it says that it can't pmount sda1 because it is already mounted as /media/usbdisk/

and I can't unmount from the desktop, it seems i should open the file browser and unmount from there. Is this normal, or is there something in the config that should be changed?

---

