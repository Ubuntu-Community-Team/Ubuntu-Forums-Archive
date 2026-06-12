---
title: "Installing kubuntu-desktop is not the same as as installing from Kubuntu ISO"
date: 2007-05-09
forum: Desktop Environments
---

### Post by thikrat on 2007-05-09
Hello All,

I wanted to give Kubuntu a shot, because of my deep curiosity.  So, I followed directions and used synaptic to install Kubuntu-desktop package.  It did in fact install and now my screen on boot says kubuntu and not ubuntu but its not really important.  I still use gdm though and not kdm.

The weird part is this, if I log into a KDE session it seems as though some parts are simply "missing"  for example, when click the logout button (looks like a power button) the only option i get is to log out, there is no hibernate, lock screen, reboot, or any of the other options that show up in gnome.  I find it hard to believe these options do not exist in regular ubuntu.

I also noticed that the screen resolution was off as well as the fonts, all in all, gnome just looked better because it looked as though it had been configured, whereas kde just installed and started up.

Did I miss a step on installing KDE for ubuntu or do i need to try PURE kubuntu by installing from that ISO instead of ubuntu?

---

### Post by aysiu on 2007-05-09
> **thikrat said:**
> 
I wanted to give Kubuntu a shot, because of my deep curiosity.  So, I followed directions and used synaptic to install Kubuntu-desktop package. What directions were those? I'd never advise someone to install *kubuntu-desktop* through Synaptic. *aptitude* is a better choice, especially if you later decide to remove *kubuntu-desktop*.

> It did in fact install and now my screen on boot says kubuntu and not ubuntu but its not really important. This should help:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

> The weird part is this, if I log into a KDE session it seems as though some parts are simply "missing"  for example, when click the logout button (looks like a power button) the only option i get is to log out, there is no hibernate, lock screen, reboot, or any of the other options that show up in gnome.  I find it hard to believe these options do not exist in regular ubuntu. If you're using GDM, you won't see those options in KDE. If you want those options, switch to KDM.

> I also noticed that the screen resolution was off as well as the fonts, all in all, gnome just looked better because it looked as though it had been configured, whereas kde just installed and started up. You'd likely experience the same problems with a stock Kubuntu installation.

---

### Post by thikrat on 2007-05-10
> **aysiu said:**
> What directions were those? I'd never advise someone to install *kubuntu-desktop* through Synaptic. *aptitude* is a better choice, especially if you later decide to remove *kubuntu-desktop*. 

The directions I saw said to install kubuntu-desktop, yes i agree on your call to use aptitude or use the "orphan" thing found in apt-get since ubuntu 6.10, its a little less aggressive than aptitiude in removing packages.

> **aysiu said:**
> 
 This should help:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

 If you're using GDM, you won't see those options in KDE. If you want those options, switch to KDM.

 You'd likely experience the same problems with a stock Kubuntu installation.

I have had kubuntu installed in the past, version 6.06 I believe, and it looked much better than what i saw after doing the apt install of kubuntu-desktop.

Any other ideas?

Thanks

---

### Post by aysiu on 2007-05-10
Ideas for what?

---

### Post by Whiffle on 2007-05-10
Screen resolution should be the same since you're using the same xorg.conf.  Fonts may be messed up.  Open up a terminal, run kcontrol, and look under Appearance>Fonts.  You might be able to play with the fonts/antialiasing settings and get them looking better.  There is a thread around here about making fonts look better, i highly recommend it, especially if you're using an LCD. 

All in all it sounds like an opportunity to play around on kde-look.org :D

---

