---
title: "Screen Resolution Options"
date: 2016-09-24
forum: Desktop Environments
---

### Post by uzzo23 on 2016-09-24
I just installed Lubuntu 16.04.1 and need some other options for monitor resolution and was hoping someone here might be able to help me. If I go under preferences>monitor settings, the highest It'll let me go is 1024x768. But as you can see from the screenshot. Some of the bottom isn't showing/ cut off.



[ATTACH=CONFIG]271342[/ATTACH]

---

### Post by clint6 on 2016-10-02
Install arandr, configure your monitor with it, and save the configuration. You should have options for 1152x864 and 1280x1024. Then ```
sudo cp ~/.screenlayout/filename.sh /etc/X11/xinit/xinitrc.d
``` to make it stick on reboot.

---

### Post by gordintoronto on 2016-10-02
It might be easier for people to help you if you identified your video adapter and monitor (brand and model).

---

