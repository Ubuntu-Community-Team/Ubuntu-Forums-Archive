---
title: "Is kcontrol installed on GTK DE's ?"
date: 2011-09-13
forum: Desktop Environments
---

### Post by jhonan on 2011-09-13
I want to configure the style of Qt apps running in lubuntu.

lxappearance (Preferences/Appearance) seems to only modify GTK apps.

I *think* what I'm looking for is kcontrol, but it's not installed. I'm cautious about installing it or using in case there's a better way of doing this.

---

### Post by kerry_s on 2011-09-13
For qt3: qt3-qtconfig
For qt4: qt4-qtconfig

---

### Post by XubuRoxMySox on 2011-09-13
I don't think any Qt apps are included in default Lubuntu. It's all gtk. So Kcontrol would not be included by default either.

If you have room on your hard disk, there's no harm in installing Qt applications, but they tend to "pull in" lots of other stuff (Qt libraries that Qt apps need).

Which Qt application are you wanting to use in Lubuntu? There may be a gtk version of it that would work just as well (Xfburn, for example, works as well on my hardware as K3B did, so I choose it to replace Brasero with on fresh installs because Brasero just makes coasters, lol).

---

### Post by jhonan on 2011-09-13
Thanks for the replies.

This is a lubuntu installation on top of ubuntu 10.04 - So I've ended up with a mixture of Qt and KDE apps. Storage isn't an issue in this instance, so I don't have a problem mixing and matching. 

For example, I'm using Yakuake (pop-up temrinal) which is based on kconsole. (I prefer it over guake, because my setup doesn't favour transparency backgrounds)

But this is mainly so I can see if KDE, Qt, and openbox can all be styled in a uniform way under the one DE.

---

### Post by jhonan on 2011-09-13
> **kerry_s said:**
> For qt3: qt3-qtconfig
For qt4: qt4-qtconfig
Thanks - I've installed both of these now, but for some reason kconsole is ignoring the settings (in either qt3 or qt4)

The menu-bar in kconsole is doing this fade-in/out effect on mouseover, that I want to get rid of.

If I do 'About KDE' in kconsole, I get **'KDE 4.4.5**'

However, qt4-qtconfig tells me **'This program uses Qt version 4.6.2'**

Does this mean I've got different versions of the Qt4 libraries in effect ?

---

