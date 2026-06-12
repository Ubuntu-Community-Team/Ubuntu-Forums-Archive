---
title: "How can I install both Ubuntu and Kubuntu with Windows?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by velizarcho123 on 2010-10-24
I wanna install both Ubuntu and Kubuntu with Wubi win installer. Is this possible and how to do it?

---

### Post by krishnandu.sarkar on 2010-10-24
Yes it's possible.

Just install the two.

But you may consider installing Ubuntu and then installing kubuntu-desktop. Because Ubuntu and Kubuntu is same with just the difference in default DE they ships with(GNOME and KDE). So basically you don't want to fill your HDD with same things.

BTW if you plan to try KDE then better use Kubuntu. From personal experience I can say installing kubuntu-desktop doesn't have any problem. But the problem comes when you intend to uninstall those packages.

---

### Post by ajgreeny on 2010-10-24
> **krishnandu.sarkar said:**
> Yes it's possible.

Just install the two.

But you may consider installing Ubuntu and then installing kubuntu-desktop. Because Ubuntu and Kubuntu is same with just the difference in default DE they ships with(GNOME and KDE). So basically you don't want to fill your HDD with same things.

BTW if you plan to try KDE then better use Kubuntu. From personal experience I can say installing kubuntu-desktop doesn't have any problem. But the problem comes when you intend to uninstall those packages.
+1
This is what I always did when I started using ubuntu 5 years ago, simply because I wanted to try both DEs before I made up my mind which to use.  Now I just use gnome but add the very few KDE apps that I need one by one; they all work whichever DE you have as default.

---

### Post by bcbc on 2010-10-24
> **velizarcho123 said:**
> I wanna install both Ubuntu and Kubuntu with Wubi win installer. Is this possible and how to do it?

No, it's not possible using wubi - wubi will always uninstall the previous install when you try to install again. It's possible with some manual workarounds to preserve the first root.disk and hook it up to the second install's grub.cfg.

---

### Post by ajgreeny on 2010-10-24
Much easier to simply have both DE options on the one install, as shown in posts 2 and 3.
```
sudo apt-get install kubuntu-desktop
``` will do everything for you, then just choose at boot time from the login window's session menu.

---

### Post by bcbc on 2010-10-24
> **ajgreeny said:**
> Much easier to simply have both DE options on the one install, as shown in posts 2 and 3.
```
sudo apt-get install kubuntu-desktop
``` will do everything for you, then just choose at boot time from the login window's session menu.

Yes, but I believe post 2 said it was possible. 

I agree the only reasonable solution is to install kubuntu-desktop although I understand you get cluttered app menus. And you'll probably want to reinstall anyway when you decide on the one you want. Personally, I'd just install kubuntu first, uninstall and install ubuntu (and that way - just my personal opinion - you only have to reinstall one time).

---

