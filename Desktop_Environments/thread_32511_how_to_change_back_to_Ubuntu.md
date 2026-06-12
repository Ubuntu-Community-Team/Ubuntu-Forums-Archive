---
title: "how to change back to Ubuntu"
date: 2005-05-08
forum: Desktop Environments
---

### Post by coldrick on 2005-05-08
OK, I tried Kubuntu and it's fine, but I'd like to go back to Gnome for my default desktop. I can do this to a point, but the login screen is still Kubuntu. 

How do I set the login screen back to the Ubuntu standard?

Thanks and regards,
David

---

### Post by JonahRowley on 2005-05-08
Edit **/etc/X11/default-display-manager** to say /usr/bin/gdm and either reboot, or **sudo /etc/init.d/kdm stop** and **sudo /etc/init.d/gdm start** from the console.

---

