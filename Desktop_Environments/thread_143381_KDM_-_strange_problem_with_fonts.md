---
title: "KDM - strange problem with fonts"
date: 2006-03-12
forum: Desktop Environments
---

### Post by tgrzejsz on 2006-03-12
Hi,
I managed somehow to change fonts in kdm (I'am completely unaware of how I did it) and now some text doesn't display with the correct font and I can't see some characters from my language.
I know I can change kdm fonts in System Settings -> Login Manager -> Font, by this only sets some of the fonts visible on the login screen, namely those that I can write my login and password with and those that I can see in menus under the buttons.
The problem is with fonts for the lables for login and password boxes and with the font visible in a message box after unsuccessful login. They are different from the rest, they don't have required characters for my language and finally I don't know how to set them.

Thanks for help,

---

### Post by Klejs on 2006-03-12
I had an incident with my KDE fonts too, but in this case they all got very small even when I changed the font settings in the KDE Control Center...

---

### Post by Jucato on 2006-03-12
@tgrzejsz: Have you tried checking the Fonts in Appearances and Themes?

@Klejs: where you able to solve your problem. Different apps sometimes have different font settings. And font settings are sometimes scattered all over the place. Add that to the fact that the font settings for your user and for the root user (when you run KControl with sudo/kdesu) are different, and you could easily get lost :D

---

### Post by tgrzejsz on 2006-03-13
[QUOTE=Fenyx]@tgrzejsz: Have you tried checking the Fonts in Appearances and Themes?

Yes, those settings are ok in my setup. The interesting thing is what settings are taken into account for display of the login screen? There is nobody logged in then. So where is the config for those fonts?

-- 
Tomek

---

### Post by Jucato on 2006-03-13
I'm not entirely sure, but it might have something to do with the KDM theme that you are using. But that's only a theory.

Have you tried playing around with the Font settings in Appearances and Themes? It might be one of those. Or probably running it as root would affect the fonts in KDM. I'm running out of ideas, too. :D

---

### Post by tgrzejsz on 2006-03-15
[QUOTE=Fenyx]I'm not entirely sure, but it might have something to do with the KDM theme that you are using. But that's only a theory.

Have you tried playing around with the Font settings in Appearances and Themes? 
...

I've tried it without any results. Font settings in Appearances change fonts on my desktop, but not on the login screen. And with KDM theme I'am able to change background of some of the controls on the login screen and also of the menus, but not fonts. So no success til now.

Thanks for the answer,
Tomek

---

### Post by kalahari875 on 2006-04-16
[QUOTE=Klejs]I had an incident with my KDE fonts too, but in this case they all got very small even when I changed the font settings in the KDE Control Center...[/QUOTE]

I had this problem as well after upgrading to KDE 3.5.1 using the packages from kubuntu.org. However, I just upgraded again to 3.5.2 and the fonts are no longer tiny. :)

---

