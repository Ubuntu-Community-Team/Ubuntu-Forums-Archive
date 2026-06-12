---
title: "Filesharing Woes"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Eds on 2006-01-25
When I go to System Settings, Share and File Sharing, I enter my password and the File Sharing window loads, but its still all greyed out.

Anyone else have this problem?

This is one thing stopping me from rolling out Kubuntu on around 40 odd machines this weekend :(

---

### Post by sharke on 2006-01-25
In a terminal type kdesu kcontrol this will give you the default kde system settings and try and adjust settings.
Regards
Sharke

---

### Post by bejinxed on 2006-01-25
Ive also found that when mounting shares on another linux box try running komba2 or smb4k as root (sudo).

After reading various articles in these forums Ive been able to get folders in my /home directory shareable.  I can access it from winblows or my xbox media center, but using another linux box (both kubuntu breezy) I have to run komba2 as sudo.  I know this is a permissions problem with smbmnt (ive seen an error when not running as sudo).  I still have problems mounting shares that are on another hard drive, that is dedicated to tvshows.  I try different stuff for awhile until i get frustrated, I know it can be done and that it works, but nothing works for me lol.

BUT, I can boot knoppix, enable samba, share all drives with no problem.  I wish it was that easy in kubuntu.

---

