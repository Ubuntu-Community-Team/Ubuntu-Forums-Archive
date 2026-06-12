---
title: "Login Screen"
date: 2010-09-22
forum: Desktop Environments
---

### Post by bryanfblareunion on 2010-09-22
I have Ubuntu Lucid and I applied the Macbuntu theme. I loved the theme but wanted to switch it backto default. This worked fine except that the login screen is still Macbuntu. I managed to change the background to the original Lucid background. It is still the same maclooking button to login though. How can I change this?

---

### Post by sisco311 on 2010-09-22
Add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by bryanfblareunion on 2010-09-23
Thanks a bunch.

---

### Post by CelticDruidBob on 2010-09-24
[COLOR=Black]Awesomesauce! 

 :guitar:[/COLOR]

---

