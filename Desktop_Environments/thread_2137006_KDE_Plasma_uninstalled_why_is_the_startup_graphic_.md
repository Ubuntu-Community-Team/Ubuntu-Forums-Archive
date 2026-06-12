---
title: "KDE Plasma uninstalled: why is the startup graphic still there?"
date: 2013-04-19
forum: Desktop Environments
---

### Post by blanka32 on 2013-04-19
So i installed the KDE plasma notebook package from the software center to try out the new GUI, but I didn't like it so I took it off. I still have some graphics stuck on the KDE settings though. And I guess thats somewhat tolerable, but when I start up my laptop, instead of the traditional purple ubuntu loading screen i get the KDE gears on a gray background. Note: this is after I 'removed' the KDE package. How do I get the old startup screen back?

---

### Post by zombifier25 on 2013-04-19
That's because when KDE was installed, it made Plymouth (the program that shows Ubuntu's loading screen) to use the KDE theme. You can use a GUI program to do it (such as Ubuntu Tweak), but I recommend the CLI way, since it only requires copying and pasting these commands into the terminal. Run this command:
```
sudo update-alternatives --config default.plymouth
```
Choose the number that says ubuntu-logo. When done run:
```
sudo update-initramfs -u
```
to apply the changes.

---

### Post by matt_symes on 2013-04-19
Hi

Open a terminal and type

```
sudo update-alternatives --config default.plymouth
```

It will give you a list of splash screen. Select the one for Ubuntu

```
ubuntu-logo.plymouth
```

Then update the initramfs.

```
sudo update-initramfs -u
```

EDIT: Just beaten to the trigger :)

Kind regards

---

### Post by ibjsb4 on 2013-04-19
Just removing the Plasma package wil not remove everything, as you found out.  Thats a bunch of packages and dependencies.

Level 1
[http://packages.ubuntu.com/quantal/kde-plasma-desktop](http://packages.ubuntu.com/quantal/kde-plasma-desktop)

You should be able to remove kde with this link.
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

If you have any kde packages you would like to keep, you will have to reinstall them.  That link removes everything kde.

Edit:  Whats your opinion Matt?

---

### Post by blanka32 on 2013-04-22
So using your advice has helped. The one thing that is still missing is the 'desktop background' option from my system settings menu. It disappeared after I installed KDE and uninstalling it in its entirety did not help either. I don't know if there are other features missing that I am unaware of at this moment.

---

