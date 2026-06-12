---
title: "Automount .iso file on boot without fstab"
date: 2009-06-23
forum: General Help
---

### Post by XCan on 2009-06-23
I was wondering if there are any easy way to automount an .iso file on boot without editing the fstab file. As of now, I'm using gmountiso after each reboot to mount an .iso file, would be nice if there were some kind of script that could automount it.

---

### Post by geirha on 2009-06-23
I recommend you do add an fstab entry for it, but make it not automatically mount at boot. Consider the following fstab-entry
```
/path/to/image.iso /media/cdrom iso9660 loop,user,noauto 0 0
```

The **noauto** option means it will not be mounted automatically during boot
The **user** option means that regular users may mount it (without sudo)

So once you have that line, you can go to System -> Preferences -> Startup Applications (Sessions if you are using 8.10 or older) and add the command "mount /path/to/image.iso" to mount it when you log in.

---

### Post by XCan on 2009-06-23
Thanks geirha, this is excellent! :)

---

