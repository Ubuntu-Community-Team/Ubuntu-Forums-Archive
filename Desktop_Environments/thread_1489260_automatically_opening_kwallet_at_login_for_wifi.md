---
title: "automatically opening kwallet at login for wifi"
date: 2010-05-20
forum: Desktop Environments
---

### Post by equaeghe on 2010-05-20
Hi,

(Kubuntu 10.04 amd64)

Whenever I login at home, I want to connect to my Wifi network.
I have set (k)networkmanager such that it connects automatically when in range, but to get the Wifi password, which is stored in kwallet, I need to give a password. I would like this not to be necessary right after login (just like the wallet stays open for a short while after it is opened), so that the laptop connects to my home network without me having to enter a password again right after login.

TIA,

Erik

---

### Post by ankspo71 on 2010-05-21
Hi,
If you don't mind less security, you could tell the network manager to store your connection information in an unencrypted file. To do that right click on the network manager in the system tray, select "manage connections", click on "other" in the side bar, then click on the "connection secrets" tab.  I think it will ask for your details one last time, but not after that.

---

### Post by equaeghe on 2010-05-21
> **ankspo71 said:**
> Hi,
If you don't mind less security, you could tell the network manager to store your connection information in an unencrypted file.

That would be a reasonable option for some connections, but I have VPN connections for which I certainly want to keep the information secure. I might however try to get it to prompt me for the vpn password every time.
Thanks for the idea.

Erik

---

