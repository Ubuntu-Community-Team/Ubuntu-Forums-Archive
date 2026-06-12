---
title: "gdm suspend on idle"
date: 2010-08-24
forum: Desktop Environments
---

### Post by double1116 on 2010-08-24
Is it possible to have the machine suspend when idle at the gdm login screen? I understand it is possible when a user is logged in through the System > Preferences > Power Management controls. What is happening is that the computer is sitting at the login screen and stays on, wasting power. I'd like it to suspend/sleep after a timeout.

---

### Post by sisco311 on 2010-08-24
Add gnome-power-preferences to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-power-preferences.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The gnome-power-preferences window should show up on the GDM screen. 

Configure it how you want, then close the window and log back in.

When you're done and want the window to stop opening with GDM, run:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-power-preferences.desktop
```

---

### Post by double1116 on 2010-09-01
Works great, thanks!

---

### Post by jongkind on 2011-02-13
> **sisco311 said:**
> Add gnome-power-preferences to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-power-preferences.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The gnome-power-preferences window should show up on the GDM screen. 

Configure it how you want, then close the window and log back in.

When you're done and want the window to stop opening with GDM, run:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-power-preferences.desktop
```

Very good, it also works for me, I was looking for this for some time. After that, this made me thinking, and I found that the same can be accomplished the using the 'default' button in the gnome power management screen.

grtz.

---

### Post by rvaliant on 2011-12-02
Any way to do this in Ubuntu 11, either with lightdm or gdm?

---

