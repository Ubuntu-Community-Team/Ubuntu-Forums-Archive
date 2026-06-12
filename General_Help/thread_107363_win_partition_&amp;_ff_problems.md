---
title: "win partition &amp; ff problems"
date: 2005-12-22
forum: General Help
---

### Post by ESPOiG on 2005-12-22
i know how to get my windows partition mountd but i dont know how to get it mountd automatically at everystartup :D

sudo mkdir /media/Windows
sudo mount /dev/hda1 /media/Windows/ -t ntfs -o umask=0222

what can i do to get it mountd at boot or when i login

and also my firefox is f*kd i click it, it says loadin application firefox or sumtin and then just doesnt load WTF? so wat to i do to fix this aswell

---

### Post by cutOff on 2005-12-23
You must edit /etc/fstab file and add the proper lines in order to mount them.

You could search info at the forums.

---

### Post by Denis on 2005-12-23
The first question is answered here: [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

