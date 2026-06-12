---
title: "Xfce Thunar giving me trouble with mounted NTFS drive"
date: 2008-01-18
forum: Desktop Environments
---

### Post by HyperBaton on 2008-01-18
Hi,

I'm running Xfce and Thunar as file manager. I have a NTFS drive mounted like this in /etc/fstab:

/dev/sda5 /media/data    ntfs     defaults,umask=007,gid=ntfs       0       0

I can browse the drive just fine in a terminal, but if I use Thunar to explore the drive, Thunar always jumps back to the root level of the drive (which is /media/data) as soon as I try to access a subdirectory. For example if I want to go to /media/data/music I can see the contents of that folder for a tenth of a second and then Thunar brings me back to /media/data. I'm not getting this on any other drive, including samba network drives.

Does anyone have any suggestions what the problem (or solution) might be?

---

### Post by HyperBaton on 2008-01-18
Okay I seem to have found whats causing this... I have to set the umask so that the "other" users have execute permission. So if I set umask=007 Thunar doesnt descend into the directory. If I set umask to 006, it works just fine. But I don't understand why? Thunar is run by myself and I am a member of the ntfs group, so why would it need the execute permission bit from "others"?

---

