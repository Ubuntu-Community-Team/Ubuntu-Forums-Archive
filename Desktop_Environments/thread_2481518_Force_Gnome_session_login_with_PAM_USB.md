---
title: "Force Gnome session login with PAM USB"
date: 2022-12-01
forum: Desktop Environments
---

### Post by morningstar.fallen on 2022-12-01
I've been trying to set up USB token authentication on my home Ubuntu 22.04 desktop using the article below. Basically I'd like to achive a memory stick based authentication for my kids in a similar fashion to using a Yubikey or any other such smartcard. I just don't want to pay for the smartcard if I can help it.

 [https://linuxconfig.org/linux-authentication-login-with-usb-device](https://linuxconfig.org/linux-authentication-login-with-usb-device)

It appears to be working in the terminal for an existing session but I can't figure out whether there is a way of making the GDM prompt for a memory stick to be inserted instead of asking for a password on the login screen.

In a SUSE article I found that I could possibly try editting the /etc/pam.d/gdm file to achieve the above. 

I added "auth       sufficient      pam_usb.so" into the file but nothing's changed.

---

