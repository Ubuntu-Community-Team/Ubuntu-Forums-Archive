---
title: "Konqui must go"
date: 2006-05-11
forum: Desktop Environments
---

### Post by elamericano on 2006-05-11
I'm trying out Kubuntu for a couple weeks, and my first reaction is, Arrgh! My eyes!!

Ok, so I sorta knew that I'd want to customize the look... a lot, but I can't seem to affect the login screen or the log off screen (the one with Konqui). I changed a splash screen, but the login screen is first, and now it clashes badly.

I also had the time displaying 'date time' and after trying some settings, now it's 'time date'. It doesn't want to go back.

I know I'm just used to the Gnome menus and look, so I'll stick with it, and see what I can do.

---

### Post by elamericano on 2006-05-11
Forgot to mention. I'm also getting gargantuan button hints. I thought they were called tool tips, but I've unchecked them in at least two places, and they're still here after a reboot.

---

### Post by ltmon on 2006-05-12
1. The logout screen is not themeable, but the login screen is.  It's called a "KDM" theme.  It will be under the system administration section of "System Settings" somewhere.

2. I assume you mean the kickertips.  They are the animated ones that only appear on the taskbar (i.e. kicker)?  To get rid of them right-click on kicker, "Configure Panels" and search in there for "Enable Mouseover Effects".  Turn that off and voila.

L.

---

### Post by elamericano on 2006-05-12
Then Konqui has won :cry: 

I tried changing System Settings->Login Manager->Appearance Tab->GUI Style, but I didn't see any difference to the login screen.

#2 worked. I didn't change that at first, because I still wanted the icons to highlight on mouseover. They still do. Go figure.

Thanks. Does anyone know the control to change the login dialog?

---

### Post by ltmon on 2006-05-13
[QUOTE=elamericano]Then Konqui has won :cry: 

I tried changing System Settings->Login Manager->Appearance Tab->GUI Style, but I didn't see any difference to the login screen.
[/QUOTE]
Ahh... my bad.  I'm using Dapper (the next version) which has this functionality by default.

To install it in Breezy use: [http://kde-apps.org/content/show.php?content=37235](http://kde-apps.org/content/show.php?content=37235)

> 
#2 worked. I didn't change that at first, because I still wanted the icons to highlight on mouseover. They still do. Go figure.


Yeah.. it's badly named for historical reasons.

L.

---

### Post by nejode on 2006-05-13
Try this link:
[http://www.kde-look.org/content/show.php?content=29331](http://www.kde-look.org/content/show.php?content=29331)
Easy to install and looks clean.

---

### Post by elamericano on 2006-05-14
Thanks for the links. KDE 3.5 looks like a step up too. I've got work to do.

BTW, I'll leave the Konqui logout screen for last. I could always compile from source if I had to - although I might as well be using Gentoo at that point.

---

### Post by elamericano on 2006-05-16
Well, one can always skip the logout screen entirely by turning off confirmation. I'm not quite used to dumping out of my session so fast yet, and I can only take the default selection, but at least that stupid, amatuerish dragon is gone. =D> 

If someone knows a way to easily replace the logout image file, I would appreciate the info.

---

### Post by elamericano on 2006-05-17
The cartoon is gone. Just replace the image:

/usr/share/apps/ksmserver/pics/shutdownkonq.png

The change is effective immediately.

A logout theme would be better, but rebuilding KDE is too much work:

[http://www.kde-apps.org/content/show.php?content=37188](http://www.kde-apps.org/content/show.php?content=37188)

(Obvious Windows reference notwithstanding)

Maybe KDE 4.0 .........

---

