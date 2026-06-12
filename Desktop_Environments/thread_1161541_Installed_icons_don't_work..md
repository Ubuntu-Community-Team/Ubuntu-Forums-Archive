---
title: "Installed icons don't work."
date: 2009-05-16
forum: Desktop Environments
---

### Post by Madfoot713 on 2009-05-16
So, I've been trying to install icon sets from System > Preferences > Art Manager, but when I try to apply them from System > Appearance > Theme > Customize > Icons, instead of showing up the way they should, they look exactly like the GNOME icons. If it matters, I'm running the newest version of Ubuntu in VirtualBox under Mac OSX Leopard.

---

### Post by days_of_ruin on 2009-05-16
They must be an invalid icon set. If an icon set has errors ubuntu will fall back to the gnome icon set. If you post a link to the icon set I can
verify if it is valid or not.

---

### Post by Madfoot713 on 2009-05-18
The one I tried to use was the one on the top right of this page, Kreski-Lines: [http://art.gnome.org/themes/icon?page=2](http://art.gnome.org/themes/icon?page=2).

Thanks in advance for the help! :D

---

### Post by Nerv68 on 2009-05-26
I'm having the same problem. Could someone help?

---

### Post by Sarai the Geek on 2009-05-26
There's a problem with the icon package- I'm going through it to see if I can find the issue. In the meantime, pick a different icon set, perhaps something from gnome-look?

---

### Post by Sarai the Geek on 2009-05-26
I found the problem... some of the icon names are wacky-doodle. It's fixable, but time-consuming. Exactly how badly do you want this icon set?

---

### Post by Nerv68 on 2009-05-26
Yeah, I took a look into the packages and it looks pretty... weird. And it seems as though some other themes are that way too. I'll just get another theme.

---

### Post by Sarai the Geek on 2009-05-26
> **Nerv68 said:**
> Yeah, I took a look into the packages and it looks pretty... weird. And it seems as though some other themes are that way too. I'll just get another theme.

On the surface, it actually looks okay- that's the basic layout of icon packages in gnome. The problem is that some of the icons are improperly named, so the computer doesn't know where to look for the right icon. My best guess is that this icon package was designed for a non-debian based distro- maybe gentoo. I had an icon package like this that I really liked, and I eventually got it functional, but it took a lot of renaming and... sigh... trial and error.

---

