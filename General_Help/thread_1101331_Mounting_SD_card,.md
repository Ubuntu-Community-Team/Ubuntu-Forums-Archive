---
title: "Mounting SD card,"
date: 2009-03-20
forum: General Help
---

### Post by robfindlay on 2009-03-20
I've recently switched to fluxbox as i have a slower machine, and i hate having to invoke nautilus everytime I want to have an SD card auto-mounted, can someone tell me what the mount command would be? 

From, /var/log/messages/
Mar 20 05:27:55 slag-desktop hald: mounted /dev/sdd1 on behalf of uid 1000
Mar 20 05:28:10 slag-desktop hald: unmounted /dev/sdd1 from '/media/disk-2' on behalf of uid 0

Obviously the card is /dev/sdd1 i can just never seem to get the cmd line syntax down to make it work just right. 

Thanks in advance guys!

-Rob

---

### Post by ddrichardson on 2009-03-20
If its vfat (which it probably is):```
mount -t vfat /dev/sdd1 /media/disk-2
```

---

### Post by robfindlay on 2009-03-20
A corollary question...whenever you execute nautilus it "overwrites" your wallpaper--in this case fluxbox's wallpaper--with the gnome wallpaper, even after killing nautilus it leaves the gnome wallpaper.

I checked the nautilus man file and could not find a switch to repress this, 

Other then rerunning fbsetbg is there a way to recover your "lost" wallpaper?

Thanks guys!

-Rob

---

