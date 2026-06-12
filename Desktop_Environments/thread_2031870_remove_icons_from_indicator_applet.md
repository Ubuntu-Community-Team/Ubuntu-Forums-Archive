---
title: "remove icons from indicator applet"
date: 2012-07-22
forum: Desktop Environments
---

### Post by erezson on 2012-07-22
Hi,

Is there an option to remove the icons I've marked in the attached img?

---

### Post by Frogs Hair on 2012-07-22
User Name: Open the software center and install dconf editor. Open the application from dash, select apps > indicator-session and remove the check show real name on panel. Logout and back in.    

Envelope: ```
sudo apt-get remove indicator-messages
```This will remove every thing listed under it ,but it can be reinstalled if you change your mind. Log out or restart after removal. The Bluetooth icon has never appeared on my panel.

---

### Post by Frogs Hair on 2012-07-22
If you open system settings , under Bluetooth there is a visibility  on/off setting. This may be for the panel indicator.

---

### Post by erezson on 2012-07-23
Thanks!

---

