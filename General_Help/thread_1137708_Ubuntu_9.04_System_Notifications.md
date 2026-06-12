---
title: "Ubuntu 9.04 System Notifications"
date: 2009-04-25
forum: General Help
---

### Post by dmillerw on 2009-04-25
Just installed 9.04, have Compiz and my NVIDIA drivers running, but I'm not getting any of the system notifications I'm supposed to.

Do I have to enable them?

---

### Post by ajmctaggart on 2009-04-25
exactly what are you looking for?  Did you see anything like "Network established" ?

---

### Post by blackened on 2009-04-25
They are supposed to be enabled by default. Being a new feature though, I'm sure there will be some bugs left over.

---

### Post by dmillerw on 2009-04-25
> **ajmctaggart said:**
> exactly what are you looking for?  Did you see anything like "Network established" ?

Nope, nothing has come up.

What applications utilize the new system notifications, anyone know?

---

### Post by dmillerw on 2009-04-25
OK, its started working, anyone know how to get Skype and Thunderbird to work with it?

---

### Post by CK05 on 2009-04-26
Yes!

[https://addons.mozilla.org/en-US/thunderbird/addon/11530](https://addons.mozilla.org/en-US/thunderbird/addon/11530)

---

### Post by nortexoid on 2009-04-26
If you find you're having problems with the new notification system notify-osd, you can try first installing the gnome-stracciatella-session and from the login menu, select the "without Ubuntu specific components" session. It will in effect disable notify-osd and use the more familiar notification-daemon system instead.

If that doesn't work just remove notify-osd (while retaining notification-daemon).

---

