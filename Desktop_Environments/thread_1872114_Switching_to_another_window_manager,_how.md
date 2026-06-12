---
title: "Switching to another window manager, how?"
date: 2011-10-30
forum: Desktop Environments
---

### Post by jorritTyb on 2011-10-30
I have Ubuntu 11.10 and I use lightdm to start my session. I installed other window managers (like xfce4) to try them out and compare them to Unity but they don't come in my list. I can choose between Recovery, Unity, Unity2D and User Defined or something but no other window manager. How can I get those other window managers in my list as well?

Thanks!

---

### Post by Toz on 2011-10-30
What is the contents of your /usr/share/xsessions directory? 

If there is no xfce.desktop file there, create one with the following content:
```
[Desktop Entry]
Version=1.0
Name=Xfce Session
Comment=Use this session to run Xfce as your desktop environment
Exec=startxfce4
Icon=
Type=Application
```

---

### Post by mike555 on 2011-10-30
Best to just download the Xubuntu live cd and burn it as image ,then reboot to it.
   I think you will like it .

---

