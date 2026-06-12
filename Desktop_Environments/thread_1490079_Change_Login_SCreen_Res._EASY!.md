---
title: "Change Login SCreen Res. EASY!"
date: 2010-05-21
forum: Desktop Environments
---

### Post by CompudahFreakk on 2010-05-21
Hey guys I'm new here and I found an easy way to change the resolution of the log in screen.

1.Go to System>Preferences>
2.Right Click "Monitors" and select add Launcher to Desktop
3.Press Alt+F2 and tick "Run in terminal" Into the white box copy and paste this "sudo -i nautilus" 
4.Navigate to /usr/share/gdm/autostart/LoginWindow
5. DnD (Drag and drop) or CnP (Copy and paste) the Launcher you made in Step 2 into this directory
6.Log out and you can change your screen resolution

To prevent "Monitors" from popping up at the login screen just repeat steps 3 & 4, then delete the "Monitors" launcher from the directory specified.

---

### Post by K.Mandla on 2010-05-22
Moved to Desktop Environments.

---

