---
title: "Desktop Environments For Ubuntu 16.04"
date: 2017-05-24
forum: Desktop Environments
---

### Post by blackfish2 on 2017-05-24
Someone told me that upon installing the latest Ubuntu I would be given the option to choose which desktop environment I would like to use.  That did not happen.  Then I read some articles about how to download the necessary software to get different desktop environments.  None of which worked.  I wanted to use GNOME.  Please, let me know if this thing can actually be switched to GNOME somehow.  If GNOME cannot be used here, it is time to uninstall this hot mess.  

I am running a Lenovo G50-45 and Ubuntu 16.04.2 and all the software is updated.

---

### Post by deadflowr on 2017-05-24
Install gnome
```
sudo apt install gnome-shell
```
logout
at the login screen in the username/password box it will now show an icon in the right corner.
click on the icon and it'll list every desktop environment currently installed on the machine.
select gnome and then login.

Bonus:
install gnome tweak tool and the extensions browser utility
```
sudo apt install gnome-tweak-tool chrome-gnome-shell
```
the chrome-gnome-shell package will allow you to install gnome extensions through your browser.
Gnome extensions home page:
[https://extensions.gnome.org/]("https://extensions.gnome.org/")

---

### Post by blackfish2 on 2017-05-24
This worked!  I had found other variations of this same command online and none of them worked.  This was the missing link!  Thank you!

---

