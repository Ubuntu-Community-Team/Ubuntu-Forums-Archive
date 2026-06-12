---
title: "enable-automatic-login-in-lubuntu"
date: 2016-04-29
forum: Desktop Environments
---

### Post by oui on 2016-04-29
hi

how to do that: [http://www.thegeekstuff.com/2009/07/enable-automatic-login-in-ubuntu-kubuntu/](http://www.thegeekstuff.com/2009/07/enable-automatic-login-in-ubuntu-kubuntu/)

in lubuntu?

(after finished installation: it was a netinstall using the mini-iso: I didn't see some question / option to select about it)

kind regards

---

### Post by nothingspecial on 2016-04-29
When I used Lubuntu you would edit /etc/lightdm/lightdm.conf 

I don't know if this has changed or not but a search regarding auto login and lightdm.conf might help.

Remember make a copy of any system files you want to change before you change them

```
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf_bak
```

---

### Post by BazBear on 2016-04-30
In Lubuntu 14.04 (and I'm guessing it's probably the same for 16.04 and 15.10) you do it by going to Start Menu > System Tools > Users and Groups, select a user account, then click on the Password "change" button, and then tick the box for "Don't ask for password on login".

---

