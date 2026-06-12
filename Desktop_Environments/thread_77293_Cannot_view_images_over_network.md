---
title: "Cannot view images over network"
date: 2005-10-16
forum: Desktop Environments
---

### Post by zez on 2005-10-16
I tried searching and couldn't find any answers but I cannot view images over my samba network.  I have an NT file server and when I access the files I can see thumbnails but I can't open the picture with any ubuntu apps.  Movies and music work fine.  It used to work at one time and quit so I wiped the drive and reinstalled, and I still can't view network pictures locally.  Any ideas?

---

### Post by kvidell on 2005-10-16
Am I correct in assuming you're either browsing with Konq/Naut over the network, or you've used smbclient/mount to mount the fileshare via smbfs to your harddrive and you're navigating to it and trying to view the files as local items?

What software are you using (I don't know if it's consequential or not, but it doesn't hurt to ask) to view the images? GQview? KThumb?
- Kev

---

### Post by zez on 2005-10-16
I'm using Nautilus to browse. I don't have the shares directly mounted but they are connected using whatever magic Gnome uses.  Samba networking doesn't seems to be Gnomes' strong suit.  It doesn't matter what graphic app I use, eye of gnome, gthumb, gimp, the same result.  In hoary I used to get a message that said no plugin found, now it just times out.  I can see the thumbnails though.

---

### Post by kvidell on 2005-10-16
No, apparently it isn't.. :-\
I can't even browse my Windows network.
I fired up Nautilus and wasn't given the option to view the network, so I put "smb://" in the location bar and it demanded a username and password to log in to a non-existant Domain...

Sorry :-\ I was gunna try and figure out where it was tripping up on you, but I can't even get as far as you've gotten.
- Kev

---

### Post by zez on 2005-10-16
Ok, I've given up on whatever psudeo network mounts gnome uses by default and am looking for something similar to smb4k but for gnome.  I really like gnome but since 99% of what I do is over my LAN I need good smb support.

---

