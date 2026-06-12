---
title: "Adding a new/2nd HDD"
date: 2005-11-03
forum: Desktop Environments
---

### Post by N8MAN1068 on 2005-11-03
So I added a 2nd 40gb hdd in order to have a set sharepoint for pics/mp3's for my desktop at home. I use gnome, wife uses KDE.

What I'd like, is for the 2nd hdd to appear as an icon on the desktop, but I can't figure out how to do that (like cd's and usb sticks do when added).

Also, what file system should I use? I formatted it as ResierFS, and mounted it in \mnt\, but it seems to disappear from there and go to an 'inactive' state every reboot.

ideas?

---

### Post by jvictor on 2005-11-03
I'd suggest even a fat32 partition will do .. the key here is to add an entry in /etc/fstab which is mounted at boot every time, 
[edit]
somethign like this

/dev/hdX        /media/Xtra_drive   vfat  user,auto     0       0
[/edit]
replace X with ur drive mostly hda or hdb etc and create a folder under media , also chk the filesystem type , ive given it as fat 32(vfat)

hope this helps

---

