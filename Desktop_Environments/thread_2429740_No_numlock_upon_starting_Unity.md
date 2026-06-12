---
title: "No numlock upon starting Unity"
date: 2019-10-22
forum: Desktop Environments
---

### Post by Yahoé on 2019-10-22
For a couple weeks now, the numbers are not locked on the numerical pad upon starting Unity. I have several Ubuntu 19.10 systems that are all affected. I created [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1847858](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1847858) but nobody is picking it up.

Could someone please point me to a quick fix until this bug is fixed?

---

### Post by uRock on 2019-10-22
This thread may be useful. [https://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen](https://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen)

---

### Post by ScislaC on 2019-10-30
> **Yahoé said:**
> For a couple weeks now, the numbers are not locked on the numerical pad upon starting Unity. I have several Ubuntu 19.10 systems that are all affected. I created [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1847858](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1847858) but nobody is picking it up.

I confirmed in the bug report as it broke for me as well. Possibly related, do you use any VPNs by chance? I ask because at the same time numlock on startup broke, my VPN remembering the password stopped working too. I'm curious if there's just something on starting the session that broke which might affect multiple things.

---

