---
title: "Disable autologin on persistent usb memory stick"
date: 2016-02-02
forum: Desktop Environments
---

### Post by razor7 on 2016-02-02
Hi, I have used YUMI to create a multiboot memory stick, it works greatn and also has the option to define a persisten area to your live distros to save data. In my case installed Lubuntu 15.10, and works just fine, even the persistence thingy. How can I disable llubuntu live autologin? I have edited /etc/lightdm/lightdm.conf but seems to re apply the settings needed for autologin after reboot...

Thanks!

---

### Post by sudodus on 2016-02-02
A live or persistent live system is not safe. If you make it ask for login, it will only be a false sense of security. What you need if you want security is an installed system (like installed into an internal drive, but to a USB pendrive). See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

and in addition to that you would need encryption (encrypted disk or encrypted home and swap). This should work in BIOS mode, but might be harder to get working in UEFI mode.

---

### Post by razor7 on 2016-02-02
Thanks. It's just a memory stick I use as a toolbox, not for everyday use.

---

### Post by sudodus on 2016-02-02
Why do you want to disable autologin, if it is only a toolbox?

---

### Post by C.S.Cameron on 2016-02-03
Go to System Settings, User Accounts and set up yourself as a new user.
You may have some difficulty shutting down.

---

### Post by razor7 on 2016-02-11
Wow, you're right! silly me! jeje

---

### Post by razor7 on 2016-02-11
Thanks, I had to perform steps described here [http://askubuntu.com/questions/155123/how-can-i-disable-automatic-login-on-a-liveusb/199740#199740](http://askubuntu.com/questions/155123/how-can-i-disable-automatic-login-on-a-liveusb/199740#199740)

---

