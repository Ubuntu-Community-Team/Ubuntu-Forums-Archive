---
title: "network-manager wallet password"
date: 2006-10-26
forum: Desktop Environments
---

### Post by finite9 on 2006-10-26
I installed network manager and run my broadcom over WPA but when connecting the first time, nm-applet asked me for a wallt password to store the router WPA password, and I assumed that it wanted my router pass again, which is very long.

How the heck do I change the wallet password now?  I cannot find where to change it!

---

### Post by chuckao on 2006-10-30
Hi,

delete this file: ~/.gnome2/keyring/.default.keyring

And now you will create a new wallet.

I don't want to use password to open network-manager to connect in my wireless network...but i don't know to change this behavior. :(

cheers

---

### Post by finite9 on 2006-11-01
are you sure about this?  I renamed the file with prefix ~ but after reboot it didn't ask me to create a new password?

UPDATE 2006-11-10:

apt-get install gnome-keyring-manager

Start the keyring manager from SYSTEM menu and press F9 to display keys.  Delete the one for the wireless router, then logout and login again.  You will be prompted for the router password and a new master keyring password.

---

