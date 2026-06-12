---
title: "session Gnome with Xgl black screen"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by natthu on 2007-09-10
Guys,
I followed the method given on [http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")  to install compiz. I have ATI Radeon x700 graphics card. I am using restricted drivers. 
After installing xserver-xgl, and creating the startxgl.sh file, when I log in with the session 'Gnome with Xgl', I am getting a black screen with 2 blank panel bars, one at the top and other at the bottom, with the pointer; and so I cant do anything there but press Ctrl + Alt + Backspace to log out and log in again. Please help.
I am using Ubuntu 7.04

---

### Post by praet on 2007-09-13
R-echeck that script for accuracy and that it is executable.
```
sudo chmod +x /usr/bin/startxgl.sh
```

---

