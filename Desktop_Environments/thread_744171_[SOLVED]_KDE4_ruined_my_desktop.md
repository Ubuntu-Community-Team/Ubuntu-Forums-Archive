---
title: "[SOLVED] KDE4 ruined my desktop"
date: 2008-04-03
forum: Desktop Environments
---

### Post by BDNiner on 2008-04-03
I installed kde4 because the new update was released. After the install i logged out of gnome and into kde and everything seemed to work fine. So i rebooted my computer and now the login screen will not come up. I just have a light brown screen with the spinning cursor. I can go to the terminal and login. but that is about it. Any ideas on what to do?

---

### Post by warp99 on 2008-04-03
You need to boot to recovery mode remove the kde4 packages. During the boot process when Grub is loading press escape then choose recovery mode. Type the following:

```
sudo apt-get remove kdelibs5 kde4base-data kde4libs-data
```

then do the following:

```
sudo apt-get install --reinstall gdm
```

This should get you back to your previous state. Also remove the entries for kde4 from your repositories list then update. Hope this helps.

---

### Post by BDNiner on 2008-04-03
Actually i figured out the issue. I went into /etc/gdm/gdm.conf-custom to compare it another ubuntu computer in my office and there were some lines under [greeter] that were different. I guess it could not find the custom greeter that i had installed last week. I thought that was weird since the file is in the location i downloaded it to. So i backed up the file and just deleted everything under that section and rebooted and now it comes up with the default gdm theme.
Thank you for your quick response.

---

