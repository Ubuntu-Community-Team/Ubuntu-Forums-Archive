---
title: "Windows Folder Browsing From linux?"
date: 2009-06-22
forum: General Help
---

### Post by Spaceman7o on 2009-06-22
Any programs which will allow me to access my windows folders whilst using linux and allow me to transfer them? also any good file converter programs?

---

### Post by anystupidname on 2009-06-22
You can mount any NTFS volume in Ubuntu.
```
mount -t ntfs-3g [-o option[,...]]  volume mount_point
```

What kind of files are you trying to convert to what?

---

### Post by t0p on 2009-06-22
I take it you're dual-booting Windows and Ubuntu?  Well, when you're in Ubuntu, you should be able to see the Windows file system.  Let's assume your Windows partition is 60 GB.  If you look in your /media directory, you should see the Windows partition called something like **60 GB Volume**.  Ubuntu plays with NTFS just fine, so you can drag files from Windows to Ubuntu and from Ubuntu to Windows, just like the Windows partition is any mounted drive.

I don't know if the Windows partition will be mounted by default or if you will need to install the **NTFS-3G** package first. (Sorry, it's been a while since I had Windows on my machine.)

---

