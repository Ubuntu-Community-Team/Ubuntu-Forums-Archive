---
title: "How do you have multiple desktop managers?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Sethiano on 2006-05-31
I'm intressed in having the options to choose between diffrent "desktop managers" like Gnome, KDE, Fluxbox (even if this is only a "window manager, I'm I right?) in the GDM before I log in. It would also be really cool if you could choose a "xgl-session" before you log in.

Now, how do I do this in Dapper Drake (if it's possible)?

Any help is appreciated!

---

### Post by garyng on 2006-05-31
GDM allows you to choose it in the login screen(not sure if the simplified ubuntu one hide it).

However, I found it easier to just create multiple user accounts each with a different(and only) desktop manager as it seems that applications sometimes still get confused working in a multiple WM situation(those messy ~/.* files)

---

### Post by Sethiano on 2006-05-31
Another silly question... how do I "connect" a user acount to a desktop manager? 

If a for example install Fluxbox, how do I "connect" it with my user "Bob"?

---

### Post by bluevoodoo1 on 2006-05-31
[QUOTE=Sethiano]IIt would also be really cool if you could choose a "xgl-session" before you log in.[/QUOTE]

[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)

I don't think you really need separate users for different WMs/DEs... I have the following on my user account...
IceWM.desktop          jwm.desktop       xgl.desktop
enlightenment.desktop blackbox.desktop
fluxbox.desktop        kde.desktop      xfce4.desktop
gnome.desktop          openbox.desktop  xgl-kde.desktop

---

### Post by mattkenn4545 on 2006-05-31
try the command gdmflexiserver (might need to sudo it)

or edit /etc/gdm/gdm.conf-custom to have 

1=Standard and when GDM starts it will start another standard xserver

---

### Post by steveneddy on 2006-05-31
[QUOTE=Sethiano]I'm intressed in having the options to choose between diffrent "desktop managers" like Gnome, KDE, Fluxbox (even if this is only a "window manager, I'm I right?) in the GDM before I log in. It would also be really cool if you could choose a "xgl-session" before you log in.

Now, how do I do this in Dapper Drake (if it's possible)?

Any help is appreciated![/QUOTE]

If it is the same as in Breezy, just sudi apt-get install [desktop of choice] then log out to hte boot screen. Go to sessions and choose the new windows manager you just DLed. It really is that easy in Breezy and should be the same in Dapper.

I use Gnome, KDE, Fluxbox, IceWM and XFce. I can boot into them at any time from the logon screen. It's really nice to have a choice and it's cool to show your friends, too. I prefer Fluxbox for the light, fast feel I get from the environment and Gnome for all the pretty eye candy.

Check out my blog for some pics of my Gnome desktop:
steveneddy.blogspot.com

-SE

---

