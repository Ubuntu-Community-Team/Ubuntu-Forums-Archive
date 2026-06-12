---
title: "Gnome gone,KDE in its Place......"
date: 2010-02-12
forum: Desktop Environments
---

### Post by wbee on 2010-02-12
Hello,

Yesterday,using the Synaptic Package Manager,I uninstalled Evolution and downloaded Thunderbird in its place. I also downloaded Lightning as a calendar.

This morning,when I logged on,it took me to the KDE desktop. I logged on again,stopping at the password screeen,and sure enough,it was set to KDE(at the bottom of the screen),but the Gnome option was gone from the menu drop down.

So,I tried to find a software download manager to reinstall the Gnome desktop. From "software sources" to the password screen,I could not get anything to type in the space provided for the password. I went to Ubuntu software,and it showed the Synaptic Package Manager as installed. 

At the top of the "kickoff application launcher" I tried to enter the package manager,but again,it would not accept any typing.

So,how do I get the Gnome desktop option back? 

Which software package should I download once I get it to accept a password?

I don't mind having the KDE but would like to have both.

--------------

Thank you.

---

### Post by nothingspecial on 2010-02-12
```
sudo apt-get install ubuntu-desktop
```

and leave evolution where it is, just igniore it, but don`t remove it.

---

### Post by wbee on 2010-02-12
nothingspecial:

It still will not accept my password.

---

### Post by nothingspecial on 2010-02-12
Do it from recovery mode. When you see grub loading press escape and boot into a root recovery shell.

Post back if this doesn`t fix your password.

ps you don`t need the sudo in the recovery shell.

---

### Post by nothingspecial on 2010-02-12
On second thoughts, did you press enter. You don`t see your password being typed in the terminal.

---

### Post by wbee on 2010-02-12
nothingspecial,

Thank you. It worked from the recovery shell.:-)

And you were right;taking out evolution broke some connection someplace.

---

### Post by nothingspecial on 2010-02-12
Removing evolution removes gnome.

Just remove the entry from your menu and the little envelope from your panel and you won`t even know it`s there. ;)

---

