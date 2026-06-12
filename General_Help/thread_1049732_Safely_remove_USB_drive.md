---
title: "Safely remove USB drive?"
date: 2009-01-24
forum: General Help
---

### Post by aarceng on 2009-01-24
I have a USB flash drive plugged in my computer. In Windows I have to click on the icon to make it "safe to remove USB drive". Is there something similar in Ubuntu? Please tell me where and how.

---

### Post by taurus on 2009-01-24
There should be an icon on your desktop.  Click it with the right button and use the option **Unmount Volume** to unmount it.

---

### Post by x33a on 2009-01-24
note: even after unmounting, the pen-drive or mp3 player light stays on. don't worry, it's not a bug, just a feature.

---

### Post by Mud.Knee.Havoc on 2009-01-24
> **taurus said:**
> There should be an icon on your desktop.  Click it with the right button and use the option **Unmount Volume** to unmount it.

Or, if you're like me and hate stuff on your desktop (one of the first things I do after install is disable displaying mounted drives on the desktop), you can just open up Nautilus and right click the usb drive and choose to unmount it.

---

### Post by blackened on 2009-01-24
> **Mud.Knee.Havoc said:**
> Or, if you're like me and hate stuff on your desktop (one of the first things I do after install is disable displaying mounted drives on the desktop), you can just open up Nautilus and right click the usb drive and choose to unmount it.

True, except that nautilus opens by default in your home directory, so to get to the USB drive you would have to hit the "Computer" button in the navigation bar.

---

### Post by mb_webguy on 2009-01-24
> **blackened said:**
> True, except that nautilus opens by default in your home directory, so to get to the USB drive you would have to hit the "Computer" button in the navigation bar.

Actually, you can right-click the volume in the sidebar to unmount it.

---

### Post by blackened on 2009-01-24
> **mb_webguy said:**
> Actually, you can right-click the volume in the sidebar to unmount it.

I always forget that the sidebar is open by default. I do away with it for cleanliness, but will admit that it's useful.

---

### Post by dcstar on 2009-01-25
> **Mud.Knee.Havoc said:**
> Or, if you're like me and hate stuff on your desktop (one of the first things I do after install is disable displaying mounted drives on the desktop), you can just open up Nautilus and right click the usb drive and choose to unmount it.

Only drives **not** in your fstab file will be displayed on the desktop, so for removable drives this is a very handy reminder that they are mounted and need to be correctly unmounted before inadvertent removal.

---

### Post by Locutus_of_Borg on 2009-01-25
since i dont use nautilus, and dont like opening thunar for no reason, i edited visudo to allow mount and umount to be used without a password, then aliased mount to 'sudo mount' and unmount to 'sudo umount /media/*' 
now since all removable drives get mounted in /media, when i want to unmount something, instead of opening a file manager and clicking a bunch of things or typing strings of text into a terminal, simply the command unmount will take care of it, and as i am rather lazy, using xbindkeys, i mapped this command to ctrl+alt+u

saves me tons of seconds

---

### Post by aarceng on 2009-01-26
Thank you all. Taurus and x33a gave me what I need.

---

