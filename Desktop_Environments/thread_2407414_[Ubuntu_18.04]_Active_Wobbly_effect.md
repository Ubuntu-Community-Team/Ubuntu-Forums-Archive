---
title: "[Ubuntu 18.04] Active Wobbly effect?"
date: 2018-12-03
forum: Desktop Environments
---

### Post by phinq1910 on 2018-12-03
I am using ubuntu 18.04 LTS, I tried enable Wobbly effect but cannot. Did ubuntu 18.04 disabled it?
How can i enable wobbly effect on my desktop?

Anyone help?

---

### Post by deadflowr on 2018-12-04
Is this a fresh install of 18.04 or an upgrade from an earlier release such as 16.04?
By default 18.04 does not use compiz anymore and as such does not have any compiz effects like wobbly.

You can get it back to use compiz by running
```
sudo apt update
sudo apt install ubuntu-unity-desktop compiz-plugins compizconfig-settings-manager
```

If prompted for lightdm choose it and when the install finishes, reboot and at the login screen where your name and password go wil be an icon in the top right corner, click on that and it'll list desktop sessions you can run.
Choose unity and proceed to login.

Here's a cleaner description:
[https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux]("https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux")

---

### Post by phinq1910 on 2018-12-04
I m fresh install. 

Thank you very much for your help!

:KS

---

### Post by deadflowr on 2018-12-04
Once you're set and logged into unity you can access the settings manager by opening the menu (the top icon in the launcher panel on the left.)
And then just type ccsm and the settings will show.

---

