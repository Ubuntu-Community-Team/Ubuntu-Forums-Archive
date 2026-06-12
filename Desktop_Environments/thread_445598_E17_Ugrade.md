---
title: "E17 Ugrade"
date: 2007-05-16
forum: Desktop Environments
---

### Post by DeathStar on 2007-05-16
OK I install Enlightenment E17 a while ago and was very happy with it. I had a few minor teething problems at first, but eventually got it configured exactly the way I wanted.

I recently performed and upgrade on my Ubuntu system using the Update Manager. Now, lots of things in Enlightenment have stopped working, or work in a different way.

I am running Ubuntu Edgy. Here is a list of my issues since upgrading.


#1
The menu system in E17 seems to have completely changed. Before the upgrade, I could edit the .order files to manipulate the menus, but now the .order files seem to have absolutely no relevance. Also, in the enlightenment configuration panel, the option for configuring "Application Menus" has completely disappeared! The only way I can edit the menus now is by using the Gnome Menu Layout tool (alacarte), but this isn't very reliable in E17.


#2
The toolbars in applications used to be very small, and I had to write a .gtkrc-2.0 to specify the font size of the application toolbars. Now, this .gtkrc-2.0 file doesn't do anything and the application toolbar text size is different depending on the application. As an example, Firefox looks fine, but if I open another application like Gnometris, the tollbar text istiny and I can barely read it. If I edit the .gtkrc-2.0 file to specify a bigger font size, Gnometris will look OK, but then Firefox looks massive!


# 3
I can no longer drag items onto the iBar. If I do this, all the icons disappear.


#4
The "Files" file browser in the E17 menu doesn't work anymore. It just shows the .desktop entries that are set in my favorites, but clicking on them does nothing. I am not really bothered too much about this as I never use it, but it's still annoying.

Has anyone had / seen these issues? If so, does anyone know a way to resolve any of them. I love using E17, but to be honest, I am going to scrap it if I can't figure this out because I can't customise it anymore!

Thanks in advance.
DS.

---

### Post by Tesiph on 2007-05-16
E17 is currently in a somewhat broken state. Only option is to either wait (untill the switch to Efreet is complete) or install a previous version.

---

### Post by DeathStar on 2007-05-16
Hi Tesiph,

Thanks for your reply. It was starting to drivve me mad. At least I know that I'm not crazy now!

For those who still have an old version of the E17 package, my advice would be to disable the E17 repositories from your sources list, so that you can perform upgrades without breaking E17. I think that's what I'll do in future, and just re-enable them whever I want to upgrade E17 (when I know it's safe)!

DS

---

### Post by worldwithoutgurus on 2007-05-16
I'm using Ubuntu Feisty + E17 CVS. 

Everything works fine except one module (language) that doesn't show up in Module Settings.

It seems like you're using an outdated version of Enlightenment.

---

### Post by hollowhead on 2007-05-16
I've had problems with E17 since i upgraded (still using 6.06 although I'm planning to upgrade to 6.1 then feisty).  I cannot do anything basic i.e. using desktop menus w/o a crash.  I'm just going to try upgrading in few months time when hopefully its a better build.....

---

### Post by jharbert on 2007-05-16
Runs fine for me.  Try this using [these]("http://ubuntuforums.org/showthread.php?t=319336") instructions to install.

---

