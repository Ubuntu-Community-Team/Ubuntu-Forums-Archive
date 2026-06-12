---
title: "Gnome + volume names"
date: 2005-05-10
forum: Desktop Environments
---

### Post by fluxus on 2005-05-10
Hi,
does anybody know how to change the volume names of gnome-volume-manager to custom ones? They are know only reflecting the size of the volumes like "50G Medium"  but I wan't to change them to something more meaningful.

---

### Post by Ptero-4 on 2005-05-10
[QUOTE=fluxus]Hi,
does anybody know how to change the volume names of gnome-volume-manager to custom ones? They are know only reflecting the size of the volumes like "50G Medium"  but I wan't to change them to something more meaningful.[/QUOTE]
 The names of the volumes are the volume's mount point. You can change the name by changing the mountpoint name and updating the required entry in /etc/fstab (requires root access for both). You can't add spaces to the names, not even by escaping them with a "\" (Linux limitation).

---

### Post by infinito on 2005-05-11
[QUOTE=fluxus]Hi,
does anybody know how to change the volume names of gnome-volume-manager to custom ones? They are know only reflecting the size of the volumes like "50G Medium"  but I wan't to change them to something more meaningful.[/QUOTE]
 Maybe you should take a look here: [http://ubuntuforums.org/showthread.php?t=27087](http://ubuntuforums.org/showthread.php?t=27087)

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=fluxus]Hi,
does anybody know how to change the volume names of gnome-volume-manager to custom ones? They are know only reflecting the size of the volumes like "50G Medium"  but I wan't to change them to something more meaningful.[/QUOTE]
 As Infinito points out, this is a well-known bug. Short temporary fix: run 
sudo /etc/init.d/dbus-1 restart

---

