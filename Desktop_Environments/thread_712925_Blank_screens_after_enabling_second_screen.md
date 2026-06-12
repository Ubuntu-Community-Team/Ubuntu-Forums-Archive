---
title: "Blank screens after enabling second screen"
date: 2008-03-02
forum: Desktop Environments
---

### Post by linuxis on 2008-03-02
Hi,

I have just installed ubuntu for the first time. The first thing I have tried to do is to enable my second screen. Using the respective GUI tool, I have set everything according to the abilities of the monitor. After clicking Ok and logging off and on again, now both screens stay blank. They do not get any signal. Starting in safe VGA mode produces the same result. Right now, I am unable to do anything but reinstall.

How can I restore the display again?

Regards

---

### Post by overdrank on 2008-03-02
> **linuxis said:**
> Hi,

I have just installed ubuntu for the first time. The first thing I have tried to do is to enable my second screen. Using the respective GUI tool, I have set everything according to the abilities of the monitor. After clicking Ok and logging off and on again, now both screens stay blank. They do not get any signal. Starting in safe VGA mode produces the same result. Right now, I am unable to do anything but reinstall.

How can I restore the display again?

Regards

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

