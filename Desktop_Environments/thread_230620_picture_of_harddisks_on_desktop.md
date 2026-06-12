---
title: "picture of harddisks on desktop"
date: 2006-08-06
forum: Desktop Environments
---

### Post by ertai on 2006-08-06
Hi,

I have a ntfs-partition on my computer for windows. And it is constantly on my desktop with a link. But I want to remove the link. The harddisk has to remain mounted but I don't want a link on my desktop. Only in nautulis.

Does anyone know how I do that?

---

### Post by Ramses de Norre on 2006-08-06
```
gconf-editor /apps/nautilus/desktop
```
and uncheck "volumes_visible".

---

### Post by orb9220 on 2006-08-06
That option will also hide an inserted cd. In my case I wanted the inserted cd icon to show when I inserted one so the gconf-editor trick won't work.

If you just want to hide the ntfs then go to home folder and create a folder which I created one called Drives. Then go in folders and create one called hda1 if that is your ntfs drive.

Then open a term
sudo gedit /etc/fstab
Find your ntfs line and modify

/dev/hda1  [COLOR="Red"]/home/orb/Drives/hda1/[/COLOR]  ntfs defaults,nls=utf8,umask=007,gid=46 0       0

and save then relogon or reboot and it should now be accesed in your home folder and cd inserted will still work on the desktop

Hope this helped.

Be careful of case-sensitive creating folders as I put drives instead of Drives in my fstab and had to go back and fix.

---

