---
title: "Both CD-drives jams after I copy stuff!!!"
date: 2005-11-03
forum: Desktop Environments
---

### Post by SunshineSmile on 2005-11-03
Both my CD RW driver and my DVD player won't eject my CDs after I have copied the stuff onto my comp with simple cut'n paste. 

It kinda sux having to reboot to copy stuff from my cds, seeing as there is quite a few, made backups before converting to Ubuntu.

Anybody with some clues about what I should check out? THIS SHIT IS DRIVING ME INSANE!!!](*,)

EDIT: strangely, the command sudo eject /dev/cdrom works fine. How come none of the drives react when I push the button on the hardware? Anybody able to make a guess?

---

### Post by Lambert on 2005-11-03
Linux is a little different in that you can not open the drive until it's unmounted like you did with the sudo eject command. You can also use sudo umount <path> which will unmount the drive and then you can hit the drive button to eject the media.

There's usually a desktop icon for me when a drive is mounted. I simply right click and then eject on the context menu.

---

