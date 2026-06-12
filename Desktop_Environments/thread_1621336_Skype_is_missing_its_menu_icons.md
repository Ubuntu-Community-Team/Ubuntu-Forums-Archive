---
title: "Skype is missing its menu icons"
date: 2010-11-14
forum: Desktop Environments
---

### Post by sashoalm on 2010-11-14
Hello everyone, I installed Xubuntu Maverick Meerkat recently, and I have a minor issue, Skype is missing its menu icons. It looks like this:
[IMG]http://img263.imageshack.us/img263/3250/screenshot1114201003241.png[/IMG]

I have checked 'show menu icons' option in Xubuntu settings, and all gtk apps have their icons. Skype is a Qt app however. VLC is also a Qt app, and it's missing its icons, too.

---

### Post by hellnest on 2010-11-14
> **sashoalm said:**
> Hello everyone, I installed Xubuntu Maverick Meerkat recently, and I have a minor issue, Skype is missing its menu icons. It looks like this:
[IMG]http://img263.imageshack.us/img263/3250/screenshot1114201003241.png[/IMG]

I have checked 'show menu icons' option in Xubuntu settings, and all gtk apps have their icons. Skype is a Qt app however. VLC is also a Qt app, and it's missing its icons, too.

Check if the gtk2-engines-qtcurve is installed and also try to reinstall the application :)

---

### Post by sashoalm on 2010-11-14
Doesn't qtcurve require KDE? I'm currently on Xubuntu, not Kubuntu.

---

### Post by dda on 2011-11-15
Have you resolved it? I see the same on Ubuntu, 10.04. Never saw this before...

---

### Post by billwest9 on 2011-12-23
I have the same problem on Debian Wheezy with Skype 2.2 beta and Gnome 3 desktop. Interestingly, if I start Skype from the command line as root, the icons are there. I cannot find the image files for the icons, so I assume they are embedded in the Skype program somewhere, and that they are being disabled by some Gnome configuration that is user specific. Have no clue what that might be, however.

---

### Post by stozher on 2012-02-01
Same issue with Gnome 3 at Debian... solved with this commands:
```
gconftool-2 --set  --type=boolean /desktop/gnome/interface/buttons_have_icons true
gconftool-2 --set  --type=boolean /desktop/gnome/interface/menus_have_icons true
```
... and **restart** Skype!

---

