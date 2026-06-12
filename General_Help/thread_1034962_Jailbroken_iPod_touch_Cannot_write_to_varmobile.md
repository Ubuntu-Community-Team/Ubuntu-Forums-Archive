---
title: "Jailbroken iPod touch: Cannot write to /var/mobile/"
date: 2009-01-09
forum: General Help
---

### Post by Masquerade on 2009-01-09
Hey everyone. I have a successfully jailbroken iPod touch (first generation, firmware 2.2).
My problem is that i have, the ipod mounted with OpenSSH, no write access to /var/mobile. (I cannot paste or create files.)

ls -l /var/mobile/ tells me:
total 0
drwxr-xr-x 44 mobile mobile 1496 Jan 5 22:50 Applications/
drwxr-xr-x 4 mobile mobile 204 Jan 6 17:30 Documents/
drwxr-xr-x 2 root mobile 68 Jan 6 21:01 Glitter/
drwxr-xr-x 38 mobile mobile 1394 Jan 6 22:14 Library/
drwxr-xr-x 12 mobile mobile 476 Jan 4 22:32 Media/

in another forum, ive been asked for the rights of the wallpapers. These are:
ls -l /Library/Wallpaper/
total 21684
-rw-rw-r-- 1 root admin 260827 Aug 29 2007 00_iPod.png
-rw-rw-r-- 1 root admin 12528 Aug 29 2007 00_iPod.thumbnail.png
-rw-rw-r-- 1 root admin 281412 Aug 29 2007 01_iPod.png
-rw-rw-r-- 1 root admin 13267 Aug 29 2007 01_iPod.thumbnail.png
etc..

Can someone help me with this?
Thanks a lot!
benny

---

### Post by adamlau on 2009-01-09
Try this:

```
sudo chown -R login.name /var/mobile
chmod 0700 /var/mobile
```

Where 'login.name' is your system login name.

---

### Post by Masquerade on 2009-01-09
okay, i did this, pasted a video in this directory, reinstalled PwnPlayer and now, my iPod touch doenst stoop booting. The pineapple logo is shown and after a while, the screen flickers and then, aigain the pineapple.

---

