---
title: "Configuring GTK applications (eg Firefox) to read from ~/.XCompose in Trusty"
date: 2014-05-10
forum: Desktop Environments
---

### Post by ObsequiousNewt on 2014-05-10
Previously, I did this according to the instructions at [https://wiki.kubuntu.org/ComposeKey#Configuration_for_Gtk_Applications_.28Gnome.2C_FireFox.2C_etc..29](https://wiki.kubuntu.org/ComposeKey#Configuration_for_Gtk_Applications_.28Gnome.2C_FireFox.2C_etc..29)

After updating to Trusty (which was done by actually reinstalling Trusty and then restoring my /home/ drive), no such file exists to be modified (there is no folder /etc/X11/xinit/xinput.d/), and the environment variable GTK_IM_MODULE has no effect.

Currently I can use the compose key in GTK applications, but it reads from the default configuration and not my own. How can I change this?

---

