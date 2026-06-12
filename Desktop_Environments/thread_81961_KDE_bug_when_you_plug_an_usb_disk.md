---
title: "KDE bug when you plug an usb disk"
date: 2005-10-25
forum: Desktop Environments
---

### Post by JuanC on 2005-10-25
When i plug an usb disk , konqueror open :
> media:/sda1 that is empty , the real folder is > /media/usbdisk

I hope this bug would be fixed soon.

---

### Post by cinnabar on 2005-10-25
Update your system.

---

### Post by mlomker on 2005-10-25
Mine is actually at /sda1 when I plug in a media stick.  If you want to disable that autoplay feature then you can remove the **ivman** package.

---

### Post by JuanC on 2005-10-25
[QUOTE=mlomker]Mine is actually at /sda1 when I plug in a media stick.  If you want to disable that autoplay feature then you can remove the **ivman** package.[/QUOTE]
I like the autoplay feature when insert an usb disk but i like that open the correct path of the usbdisk in my case /media/usbdisk

[QUOTE=cinnabar]
Update your system.
[/QUOTE]
I use Kubuntu Breezy Badger 5.10

---

### Post by mlomker on 2005-10-25
> I use Kubuntu Breezy Badger 5.10

Bug fixes have come through about every two days since it was released.  I think they were asking if you had run a system update recently.

---

### Post by Jengu on 2005-10-26
This problem still occurs for me with my ipod, and I'm updated to the latest and greatest. When I plug it in, it opens media:/sda1, complains it doesn't exist, then opens media:/sda2 which does. Strangely, if I go to /media/sda2 it's empty, but there's also /media/ipod which has the right files in it. media:/ipod in konqueror 'does not exist'. Unplugging and replugging multiple times seems to make it skip numbers -- I just plugged it in again and it tried to open media:/sdb1 which didn't exist and media:/sdb2 which did (like it's incrementing from last time doing sda1 and sda2).

Also, right clicking the ipod on the desktop and clicking safely remove does nothing (the ipod still thinks it's connected).

---

### Post by daller on 2005-10-26
[QUOTE=Jengu]This problem still occurs for me with my ipod, and I'm updated to the latest and greatest. When I plug it in, it opens media:/sda1, complains it doesn't exist, then opens media:/sda2 which does. Strangely, if I go to /media/sda2 it's empty, but there's also /media/ipod which has the right files in it. media:/ipod in konqueror 'does not exist'. Unplugging and replugging multiple times seems to make it skip numbers -- I just plugged it in again and it tried to open media:/sdb1 which didn't exist and media:/sdb2 which did (like it's incrementing from last time doing sda1 and sda2).

Also, right clicking the ipod on the desktop and clicking safely remove does nothing (the ipod still thinks it's connected).[/QUOTE]

You can use "sudo eject /media/ipod/" to unmount it!!!

I haven't got an ipod myself, so I suggest that you file a bugreport!

---

### Post by drspin on 2005-10-28
I have an interesting scenario -- I use my system in a true multiuser environement. If iI stay logged in then open a new session and login as a different user then log out. I'll put in my USB disk and it will mount as the last logged in user.

chwoning it doesn't work.

pumount as that other user will unmount it and I can manually remount it as myself.

This is DEFINATELY annoying... and can be easially recreated. Havent checked the bug pages to see if this was a filed bug.

I'm am not sure if this occurs in both Gnome and KDE
Cole

---

### Post by JuanC on 2005-10-29
Fixed !!!!

Today I do :
> 
# apt-get update
# apt-get upgrade


---

### Post by jeremy on 2005-10-29
But youprobably have the bug described at [http://ubuntuforums.org/showthread.php?t=83164](http://ubuntuforums.org/showthread.php?t=83164) now!

---

