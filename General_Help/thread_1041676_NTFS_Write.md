---
title: "NTFS Write"
date: 2009-01-16
forum: General Help
---

### Post by fparedesg on 2009-01-16
Hey everyone. After mounting my NTFS partition, (/media/NTFS) I try to create a folder inside it (/media/NTFS/new), I open the folder, and Nautilus brings me back to /media/NTFS. The ./new folder is nowhere to be seen. If I try to create another folder called "new", it tells me that I cannot create it because it already exists. If I check using ls with the Terminal, the new folder does appear, but it doesn't with Nautilus. I don't know what's going on... Can anyone help me?

My hard drive has 6 partitions:
sda1 = OS X
sda2 = Windows XP
sda3 = Ubuntu
sda4 = extended
sda5 = Linux Swap
sda6 = NTFS

Oh and when I checked to see if the "new" folder was there with OS X, it did appear.

Thanks to anyone that helps!!

---

### Post by 5BallJuggler on 2009-01-16
is it a hidden file for some reason,

open the "places" tab from your panel, click on computer, navigate your way to the place where the folder is stored,
click on view, then scroll down to hidden files, click on this.
What happens?

---

### Post by fparedesg on 2009-01-16
> **5BallJuggler said:**
> is it a hidden file for some reason,

open the "places" tab from your panel, click on computer, navigate your way to the place where the folder is stored,
click on view, then scroll down to hidden files, click on this.
What happens?

No...it's not hidden. I checked. Here's the terminal results after ls:
```
federico@ANCHOVA:~$ ls /media/NTFS
ls: cannot access /media/NTFS/Microsoft Office 2008 Special Media Edition (MAC-ENG): Input/output error
ls: cannot access /media/NTFS/Office Installer.mpkg: Input/output error
Colegio                                                My Games
Drivers and Kexts                                      My Music
iPod Hack                                              [COLOR="Red"]new[/COLOR]
[KAA]_FullMetal_Alchemist_01-51.DVD(complete)          Office Installer.mpkg
Microsoft Office 2008 Special Media Edition (MAC-ENG)  OSX Apps
federico@ANCHOVA:~$ 

```

---

