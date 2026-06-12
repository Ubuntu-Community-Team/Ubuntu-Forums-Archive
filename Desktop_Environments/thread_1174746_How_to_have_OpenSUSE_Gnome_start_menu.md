---
title: "How to have OpenSUSE Gnome start menu?"
date: 2009-05-31
forum: Desktop Environments
---

### Post by juanbretti on 2009-05-31
Hello,
I would like to know how can I get OpenSUSE Gnome start menu running on Ubuntu 9.04?

[IMG]http://static.opensuse.org/hosts/www.o.o/images/screenshots/zoom/1.jpg[/IMG]

Thank you!

---

### Post by fakhar on 2009-05-31
from synaptic, search for gnome-main-menu, it will also install libslab0, then add 'main menu (default menu and application browser)' to your panel

---

### Post by juanbretti on 2009-05-31
Thank you! Was just what I was looking for!

**Thanks!**

---

### Post by ajgreeny on 2009-05-31
Having used Mint, which has a similar menu, I would quite like that too, but it doesn't seem to work for me.  I have always used the main menu instead of the menu bar, and already have that on the panel, so perhaps it just needs a reboot or for me to login again to do the job.  I'll report back.

---

### Post by juanbretti on 2009-05-31
> **ajgreeny said:**
> Having used Mint, which has a similar menu, I would quite like that too, but it doesn't seem to work for me.  I have always used the main menu instead of the menu bar, and already have that on the panel, so perhaps it just needs a reboot or for me to login again to do the job.  I'll report back.

To be honest: I haven't tried yet.
As you, "I'll report back" :)

---

### Post by ajgreeny on 2009-05-31
Well, here I am reporting back.

Yes it does work after logging out and in again, but having now seen it, I don't like it at all.  It is very different to the Linux Mint menu, and instead of showing all your applications as Mint can, when you want to see "More applications" it shuts the menu down and opens a separate window on the desktop.  Very odd way to do it, I think.

Not what I wanted at all, so I will stick with the original Main menu instead.

---

### Post by Sarai the Geek on 2009-05-31
> **ajgreeny said:**
> Well, here I am reporting back.

Yes it does work after logging out and in again, but having now seen it, I don't like it at all.  It is very different to the Linux Mint menu, and instead of showing all your applications as Mint can, when you want to see "More applications" it shuts the menu down and opens a separate window on the desktop.  Very odd way to do it, I think.

Not what I wanted at all, so I will stick with the original Main menu instead.

The MintMenu from Linux Mint is compatible with Ubuntu, it works perfectly except for the "Software Manager" button.
Go to their [packages page]("http://packages.linuxmint.com/#6main") and download the following packages: **mintsystem** and **mintmenu**. You'll need to install them in that order (no worries, they're .debs!), then MintMenu appears in your list of panel applets!

---

### Post by ajgreeny on 2009-05-31
Thanks for that Sarai.  I'll give it a try later and see if I like it better than the Suse-look menu.

EDIT:  I've just had a go and there are several dependencies in the Mint7 Gloria version which are not covered by those two packages.  I could try and do it easily enough, but to be honest, I can't be bothered to keep going, I am quite happy with the ordinary main menu.
Also needed:-

mint-install
deskbar-applet
cowsay
dontzap

---

### Post by Sarai the Geek on 2009-05-31
> **ajgreeny said:**
> Thanks for that Sarai.  I'll give it a try later and see if I like it better than the Suse-look menu.

EDIT:  I've just had a go and there are several dependencies in the Mint7 Gloria version which are not covered by those two packages.  I could try and do it easily enough, but to be honest, I can't be bothered to keep going, I am quite happy with the ordinary main menu.
Also needed:-

mint-install
deskbar-applet
cowsay
dontzap

Don't use the Gloria packages, it'll cause your computer to have an identity crisis! Use the Felicia packages- the link I gave was supposed to automatically scroll to the LM 6 packages. Guess it didn't. Anyway, here's the ones you need:
[mintmenu]("http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.2.2_all.deb") , [mintsystem]("http://packages.linuxmint.com/pool/main/m/mintsystem/mintsystem_6.2_all.deb")

---

### Post by ajgreeny on 2009-06-01
OK, I'll try again with the Felicia packages.  I presumed as I'm using jaunty, and mint 7 Gloria is based on jaunty, that I would need those Mint7 packages.  You link did indeed auto scroll to the Felicia packages, but I thought I was being clever, and manually chose the Gloria ones.

Ah well, I can't always be right, can I?
Thanks again.

---

### Post by Sarai the Geek on 2009-06-01
> **ajgreeny said:**
> Ah well, I can't always be right, can I?
Thanks again.

Haha, don't be too hard on yourself- nobody's right every single time!

---

