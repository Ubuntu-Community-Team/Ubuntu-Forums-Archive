---
title: "How do I install XFCE and only XFCE? [Resolved]"
date: 2007-04-24
forum: Desktop Environments
---

### Post by michwill on 2007-04-24
Hi all,

I'm interested in all steps necessary to install XFCE and only XFCE.  I don't want to install Xubuntu because of all the fluff that gets installed with it.  I don't need cups, I don't need abi-word, I don't need any of that stuff.  I simply want to install and start a simple window manager (XFCE).  Please provide a link or instructions.

Thanks in advance!

---

### Post by taurus on 2007-04-24
```
sudo aptitude update
sudo aptitude install xfce4
```

---

### Post by michwill on 2007-04-24
Thanks, I tried that, but couldn't start it.  I kept getting X related errors.  What's the proper setup/procedure for starting it?

---

### Post by aysiu on 2007-04-24
Are you starting from a command-line system? Or do you already have Gnome and/or KDE installed?

---

### Post by michwill on 2007-04-24
No other window managers are installed


STEPS:

[I]
1.  Install Feisty Alternate

2.  apt-get update

3.  apt-get upgrade

4.  reboot

5.  apt-get dist-upgrade

6.  reboot

7.  apt-get install -y xfce4

8.  reboot once more for good measure

9.  starxfce  (get errors)


[/I]

. . .I'm not sure what I need to be doing.  Obviously if I install Xubuntu all works fine, but as I said, I'm not interested in all of the "fluff"

---

### Post by aysiu on 2007-04-24
Ah, then you want this: ```
sudo apt-get update
sudo apt-get install xorg xfce4 gdm
sudo /etc/init.d/gdm start
``` No need to reboot.

---

### Post by michwill on 2007-04-24
Excellent, thank you!

---

