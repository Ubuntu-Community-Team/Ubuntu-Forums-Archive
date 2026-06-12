---
title: "Open Office Icons Disappear"
date: 2006-06-04
forum: Desktop Environments
---

### Post by bsell on 2006-06-04
I installed the Ubuntu desktop today in Kubuntu Dapper. When I opened OpenOffice apps, the icons disappear. You can roll over them and they will reappear for a moment, but then disappear. The same is true for the menu bar -- clicking on the menus causes the other menu items to disappear. 

I tried to reinstall OOo using Synaptic, but to no avail. This happens only in OOo AFAIK. 

Any ideas on how to keep the icons from disappearing?

---

### Post by edoardo on 2006-06-19
[QUOTE=bsell]I installed the Ubuntu desktop today in Kubuntu Dapper. When I opened OpenOffice apps, the icons disappear. You can roll over them and they will reappear for a moment, but then disappear. The same is true for the menu bar -- clicking on the menus causes the other menu items to disappear. 

I tried to reinstall OOo using Synaptic, but to no avail. This happens only in OOo AFAIK. 

Any ideas on how to keep the icons from disappearing?[/QUOTE]

same problem here after installing Kubuntu desktop in Ubuntu Dapper

---

### Post by dirvine on 2006-06-21
[QUOTE=bsell]I installed the Ubuntu desktop today in Kubuntu Dapper. When I opened OpenOffice apps, the icons disappear. You can roll over them and they will reappear for a moment, but then disappear. The same is true for the menu bar -- clicking on the menus causes the other menu items to disappear. 

I tried to reinstall OOo using Synaptic, but to no avail. This happens only in OOo AFAIK. 

Any ideas on how to keep the icons from disappearing?[/QUOTE]

I have exaclty same issue. Noted after some kde stuff was installed - its annoying.

---

### Post by edoardo on 2006-06-21
[QUOTE=dirvine]I have exaclty same issue. Noted after some kde stuff was installed - its annoying.[/QUOTE]

I used synaptic to remove the KDE Integration for OpenOffice.org package
openoffice.org-kde 

it's certainly fails to work if you also have selected the gtk-qt engine in KDE control  panel for the lokk & feel of gtk applications

---

### Post by edoardo on 2006-06-21
submitted as a bug

[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/50581](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/50581)

---

### Post by Kimos on 2007-11-16
Zombie thread, but I just wanted to post a reply.

I had a missing icon problem in OO under Gnome. Turns out it was when I changed my theme for icons and such, the icon set for OO was missing. Fixed it with:

```
apt-get install openoffice.org-style-crystal
```

---

### Post by begeland on 2007-11-26
I just added openoffice-kde package in synaptic and fixed the problem.  This is opposite, but achieved the same results, as a previous post.  (I'm running Kubuntu 7.10).

---

### Post by bb002 on 2007-12-05
Who says posting in zombie threads is pointless.
I was having this exact issue in Gutsy until just now! Too bad you didn't post this 3 weeks ago when I was trying to figure it out. Only thing I didn't do was install a different icon theme for OpenOffice. 

Thanks a lot, though I was beginning to get used to the text only menus!

[edit]
btw. My station is a fresh install of Gutsy with all updates applied. I have a different desktop icon theme which seems to affect openoffice's icons as well. But i don't use OO that much to stick with the default desktop Icon theme.

However my laptop which is a fiesty install that i dist-upgrade'd through the Gutsy Beta process isn't affected by this problem at all. Kinda odd if I do say so myself.

---

### Post by jpantone on 2007-12-21
When I upgraded to Gutsy using the update manager, the icons dissapeared from the toolbars. I solved the problem by using Synaptic to install all of the OpenOffice Style packages (default, chrystal, industrial, etc.) which for some reason weren't already installed.

Bug in the update to new version of distro?

John

---

### Post by cdean on 2007-12-24
After I installed blubuntu-look, the icons disappeared. I'm not sure which icon set it uses, but installing openoffice.org-style-andromeda, openoffice.org-style-default, and openoffice.org-style-tango fixed it.

---

### Post by biodiesel-bri on 2007-12-27
Had the same problem here - installing openoffice.org-style-default and  openoffice.org-style-crystal brought the icons back.

Thanks for posting the solution!

---

