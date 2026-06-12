---
title: "Can this be done from the Live CD?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by darthvivi on 2006-07-22
I'm trying to fix my grandpa's computer, and Windows XP is completely messed up. So I'm going to reformat it, but first I need to backup the "My Pictures" folder from Windows. It's over 4 GB (also has my aunts pictures on it) so I'm wanting to burn it to DVD.

Is there a way to do that from my Dapper Drake Live CD (without installing Ubuntu), since it seems to be impossible in Windows?

---

### Post by mlind on 2006-07-22
I'm not sure about DVD burning, but you should be able to do this using Ubuntu install cd (LiveCD). At least it's woth a try. 
Boot with install cd, install burning application like k3b or xcdroast and try if it works.

---

### Post by arkangel on 2006-07-22
run the live cd  and in places menu  should appears  your HD  then burn  using some application ,  i normally use gnomebaker

---

### Post by aysiu on 2006-07-22
Unlike Knoppix, Ubuntu's live CD will probably give you some kind of *pmount* or "permission denied" error when you try to open the Windows partition.

You have to mount it properly first in order to access the files. Assuming it's /dev/hda1 and NTFS: ```
sudo mkdir /recovery
sudo mount -t ntfs /dev/hda1 /recovery -o nls=utf8,umask=0222
``` If it's not /dev/hda1 (or you're not sure) and not NTFS, let us know, and we'll help you to get it mounted.

If you have a Knoppix CD lying around, use that instead.

Don't install any programs, as the more installed programs you have during a live session, the less RAM you have available. Both Kubuntu and Ubuntu have CD-burning programs built into them. I would assume Nautilus can burn DVDs, too, but I'm not sure.

---

