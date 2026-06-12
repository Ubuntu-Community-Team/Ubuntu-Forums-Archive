---
title: "How change login appearance?"
date: 2011-05-13
forum: Desktop Environments
---

### Post by jacqueshappy on 2011-05-13
Hi I want to change the appearance of my login screen and a little research has shown me that I need something called gdm? 
How do I get this on ubuntu 10.10? I can't find it in software centre

---

### Post by stinkeye on 2011-05-13
Gdm is the login manager installed by default and is not as customizable as what was used before.

You can change your login background, theme, etc by entering in the terminal
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Log out then select the style you want at the login from the Appearance window that pops up.
This will only affect the login appearance.


Then log in and execute 
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
to remove gnome-appearance-properties from the login window.

---

### Post by jacqueshappy on 2011-05-14
Many thanks!

---

