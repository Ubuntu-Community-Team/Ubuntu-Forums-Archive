---
title: "Log in window missing from computer."
date: 2017-04-15
forum: Desktop Environments
---

### Post by ChuckyZ28 on 2017-04-15
I just installed some updates and the format on my log in screen is all messed up, I can not even see the log in screen. I can post a picture, however it is not very good because it is from a cell phone.

---

### Post by ChuckyZ28 on 2017-04-15
[ATTACH=CONFIG]274569[/ATTACH]

I have absolutely no idea why the forum flipped the picture upside down.

---

### Post by Frogs Hair on 2017-04-17
Try logging in to TTY using Ctrl +Alt + F1 . Login, enter password, and try the following and reboot.```
sudo dpkg-reconfigure -a lightdm-gtk-greeter
```

---

