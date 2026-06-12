---
title: "usb harddrive stopped being automounted"
date: 2005-06-03
forum: Desktop Environments
---

### Post by cabrito on 2005-06-03
hi!

i am running a hoary (installed first warty and did a dist-upgrade) on my laptop and i have a USB external harddrive. It was automounted all the time without any  problems until one day i unmounted the device manually (right mouse click on desktop icon -> unmount).

Since then all other USB devices are still automounted but not the harddrive. It seems to me that there is an entry somewhere that tell the gnome-volume-manager not to mount that specific device but i havent been able to find anything.

In the meantime i've edited my fstab so it automounts /dev/sda1 to /media/harddrive/ but that is rather statical (in case i plug my webcam first, being for example sda1, then the harddrive would not be mounted).

can someone give me a hint on how to restore it?

thx!

---

### Post by braunsfeld on 2005-06-03
What does dmesg say when you plug it in?

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=cabrito]hi!

i am running a hoary (installed first warty and did a dist-upgrade) on my laptop and i have a USB external harddrive. It was automounted all the time without any  problems until one day i unmounted the device manually (right mouse click on desktop icon -> unmount).

Since then all other USB devices are still automounted but not the harddrive. It seems to me that there is an entry somewhere that tell the gnome-volume-manager not to mount that specific device but i havent been able to find anything.

In the meantime i've edited my fstab so it automounts /dev/sda1 to /media/harddrive/ but that is rather statical (in case i plug my webcam first, being for example sda1, then the harddrive would not be mounted).

can someone give me a hint on how to restore it?

thx![/QUOTE]
 Can be the infamous [Hal/DBUS bug](http://ubuntuforums.org/showthread.php?t=27087)

---

### Post by cabrito on 2005-06-03
hi!

after a few tries commenting and uncommenting the line in fstab and plugging the harddrive and a usb memory key now everything seems to work again. I am sure this morning the harddrive did NOT mount automatically when i plugged it in unless i had the line in fstab.

I have just tried to reproduce the error but i unmounted the volume and now it keep mounting so i do not know what happened exactly.... ???

---

