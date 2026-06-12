---
title: "seeing a windows computer on the network"
date: 2005-12-15
forum: General Help
---

### Post by renzokuken on 2005-12-15
i have a small home network of two XP computers and my Ubuntu box, all connected to a LAN via a linksys router

how can i see and open the files being shared on the two XP computers (and possibly vice versa)

thanks

---

### Post by earobinson on 2005-12-15
I searched the forums for (windows network shared) and found this [http://www.ubuntuforums.org/showthread.php?t=103328&highlight=network+windows+shared](http://www.ubuntuforums.org/showthread.php?t=103328&highlight=network+windows+shared)

---

### Post by renzokuken on 2005-12-15
awesome, thanks....i didnt find that one on my searches

thats the question of sharing a linux folder to XP users,

so does anyone know how a ubuntu user (XFCE4) can see the shared folders on and XP machine?

---

### Post by earobinson on 2005-12-15
for that i searched (see windows shared folders) and found
[http://www.ubuntuforums.org/showthread.php?t=100671&highlight=windows+shared+folders](http://www.ubuntuforums.org/showthread.php?t=100671&highlight=windows+shared+folders)

---

### Post by renzokuken on 2005-12-15
i'm probably being an idiot here but i dont see how that helps (the thread or the guide) are they again not for allowing windows users to see my linux files???

---

### Post by earobinson on 2005-12-15
> I normally access it through alt+F2 smb://ADDESK
More reading:
[http://www.ubuntuforums.org/showthread.php?t=83300&highlight=smb+windows](http://www.ubuntuforums.org/showthread.php?t=83300&highlight=smb+windows)
[http://www.ubuntuforums.org/showthread.php?t=61166&highlight=smb+windows](http://www.ubuntuforums.org/showthread.php?t=61166&highlight=smb+windows)
(I have never done this before but there seems to be a surplus of info on the forums)

---

### Post by tanis143 on 2005-12-15
I had the same problem. Here is what I did to solve it.

Make sure all samba is installed:
I cant remember the steps exactly, but if you look in the help file, go to the getting started section, go to networking, and it has the instructions there.

After this I could see the shares, but couldn't mnt them. Here is the crucial step I found that helped:

go to console, su to root, and type these lines:

chmod u+s /usr/bin/smbmnt
chmod u+s /usr/bin/smbumount
chmod u+x /usr/bin/smbmnt
chmod u+x /usr/bin/smbumount

After this I could mnt any and all shares.

---

