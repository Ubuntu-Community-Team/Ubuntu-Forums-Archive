---
title: "Change folder access rights?"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Event Horizon on 2005-08-16
I used sudo to mount my 65 gig NTFS windows partition to /media, but when I try to access it, I get the following message:

You do not have the following permissions to read file:///media

Also, the folder icon has a big lock on it, and at the bottom of konqueror it says the folder is locked. Checking the folder properties, I discovered that the "owner" (root) can view content, and "group" and "other" are forbiddon.

Bottom line: How do I change folder permissions using sudo? I'm really new to linux so I don't know any terminal commands.

---

### Post by xaque on 2005-08-16
Just type this at the command line: 
```
sudo chown (your username):(your group) /media
```

That will give you permission rights to that folder. If you want to set the drive to mount every time you boot up your computer, you might want to look into editing your fstab file... there are hundreds of howtos on Google.

---

### Post by Event Horizon on 2005-08-16
Wow, thanks alot man.

---

