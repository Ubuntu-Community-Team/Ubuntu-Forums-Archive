---
title: "Installed UNR, Can I remove UNR but keep Ubuntu?"
date: 2009-06-03
forum: General Help
---

### Post by deadyeti on 2009-06-03
I have recently installed UNR, and I am thinking I would much rather have the desktop version of Ubuntu instead. Is my only option to reinstall, or can I remove the UNR GUI without harming the desktop portion?

I apologize if this has been answered, but I was not able to find an appropriate answer.

Thanks for the help in advance!

---

### Post by jenkinbr on 2009-06-03
You should be able to run the command```
sudo apt-get install ubuntu-desktop
``` from a terminal, or locate and install the package "ubuntu-desktop" in the package manager.

---

### Post by deadyeti on 2009-06-03
appreciate the help, thanks much.

---

### Post by jenkinbr on 2009-06-03
Your very welcome.  Multiple desktop environments can co-exsit on the same system.  On the login screen, you may need to change your default session to be gnome instead of UNR, if it wasn't done automatically.

---

### Post by redbook4574 on 2009-06-03
> **jenkinbr said:**
> You should be able to run the command```
sudo apt-get install ubuntu-desktop
``` from a terminal, or locate and install the package "ubuntu-desktop" in the package manager.

You should not need to install ubuntu-desktop, in 9.04 it is already there,
Simply go to system-preferences and you will see Switch-Desktop, this will change you to a standard ubuntu desktop.. If you then leave it in ubuntu-desktop on shutdown it will return to gnome desktop on boot. Hope this helps.

---

