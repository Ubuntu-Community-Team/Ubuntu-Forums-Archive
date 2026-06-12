---
title: "Disable user change wallpaper."
date: 2014-11-13
forum: Desktop Environments
---

### Post by kjlorenzo on 2014-11-13
Hi! I installed ubuntu 14.04 in office pc's and create a gschema override file to custom enterprise logo and wallpaper.

[B][org.gnome.desktop.background]
show-desktop-icons=true
picture-uri='file:///usr/share/backgrounds/social.png'

[org.gnome.desktop.interface]
buttons-have-icons=true
menus-have-icons=true

[com.canonical.unity-greeter]
draw-grid=false
draw-user-backgrounds=false
logo= "/usr/share/unity-greeter/social-logo.png"
background="/usr/share/backgrounds/social.png"
background-logo="/usr/share/unity-greeter/social-cof.png"[/B]

All work fine, but the user's can change de wallpaper and I don't want.

In ubuntu 12.04 I use gconf2-tool --set and create a mandatory rule, but this was replaced by dconf.

I read diferent post where say user the dconf locks.
 
I create a /etc/dconf/profile/**socia**l file with:
**user**[B]-db:user
system-db:division

[/B]and /etc/dconf/db/**social.d/00-social-settings** with:

**[**[B]org/gnome/desktop/background]
 picture-uri='file:///usr/share/backgrounds/social.png'[/B]

and /etc/dconf/db/social.d/**locks/picture** with:

**/org/gnome/desktop/background/picture-uri**

execute **dconf update**

But the user's can still change the wallpaper.

Can anyone help me!!!

Thank's

---

