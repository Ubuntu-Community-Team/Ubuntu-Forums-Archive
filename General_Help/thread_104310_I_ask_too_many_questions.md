---
title: "I ask too many questions"
date: 2005-12-15
forum: General Help
---

### Post by tanis143 on 2005-12-15
Ok, this maybe a simple question, but I've found nothing on it. How do you make smb keep a network drive mounted even after a reboot?

---

### Post by Sionide on 2005-12-15
Add it your fstab - I don't know the specifics but that is what you have to do. Be careful when editing your fstab though. Do not muck it up :S

---

### Post by tanis143 on 2005-12-15
lol If I knew how fstab worked or what it was I would understand. Time to google search it....

---

### Post by Kevinator on 2005-12-15
man fstab.

Also check out man mount.

As the man page will tell you, fstab itself lives in /etc/fstab. You'll need to sudo to edit it.

---

### Post by cstudent on 2005-12-15
Click on Places>>Connect to Server and enter the IP (or name) of the computer you want to connect to along with the share name, etc. This will put an icon on your desktop to that share that will stick even when you reboot. To get rid of it, just right click on the icon and select unmount volume.

---

