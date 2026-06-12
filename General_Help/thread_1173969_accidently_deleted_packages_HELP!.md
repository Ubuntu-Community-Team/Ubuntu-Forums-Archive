---
title: "accidently deleted packages HELP!"
date: 2009-05-30
forum: General Help
---

### Post by Prelude203 on 2009-05-30
please help,

i accidently deleted the package 'gnome-keyring' and when i did it deleted about 10 - 20 other packages and my system is missing a lot of things now... does anyone know what packages i have to reinstall or is there a way to to a system restore type of thing like in windows?

---

### Post by vishy1618 on 2009-05-30
Good grief! Well, try installing gnome-keyring again(I dont know if you would be able to do that, as you might not even have GDM any more!). If you can't then the only good alternative would be to back up and reinstall ubuntu.

---

### Post by Yellow Pasque on 2009-05-30
This command should get you back up and running:
```
sudo apt-get install gnome-keyring apturl checkbox-gtk fast-user-switch-applet gdebi gdm gdm-guest-session gksu gnome-app-install gnome-codec-install gnome-keyring software-properties-gtk ubufox update-manager update-notifier usb-creator
```

To see exactly what got removed, look at /var/log/dpkg.log or /var/log/apt/term.log

---

### Post by ptn107 on 2009-05-30
Removing gnome-keyring also removes the following:

apturl
checkbox-gtk
fast-user-switch-applet
gdebi
gdm
gdm-guest-session
gksu
gnome-app-install
gnome-codec-install
network-manager-gnome
software-properties-gtk
ubufox
ubuntu-desktop
update-manager
update-notifier
usb-creator

The following command will make things right (internet connection required):
```
sudo aptitude install gnome-keyring apturl checkbox-gtk fast-user-switch-applet gdebi gdm gdm-guest-session gksu gnome-app-install gnome-codec-install network-manager-gnome software-properties-gtk ubufox ubuntu-desktop update-manager update-notifier usb-creator -y
```

---

