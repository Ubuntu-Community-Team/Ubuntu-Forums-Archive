---
title: "Question about languages in ubuntu"
date: 2004-12-25
forum: Desktop Environments
---

### Post by Programmer on 2004-12-25
Hello :-)
I have installed ubuntu and I need help with some configurations.
Now, I have only american english in the keyboard configurations, and I need help installing two more languages "Hebrew" and "Russion".

Thanks for your support :)

---

### Post by feneks on 2004-12-25
*sudo dpkg-reconfigure locales*
sets languages which can be chosen in gdm.  - gdm has to be restarted by sudo 
*/etc/init.d/gdm restart*

I think keymaps can be switched in GNOME with a panel-applet - haven't done yet.

Perhaps you will have to install cyrillic fonts. They are used in ru, isn't it?


HOWTOS:
[http://www.ubuntulinux.org/wiki/HebrewLocalizationHowto](http://www.ubuntulinux.org/wiki/HebrewLocalizationHowto)
[http://www.ubuntulinux.org/wiki/UbuntuRussianLocalizationHOWTO](http://www.ubuntulinux.org/wiki/UbuntuRussianLocalizationHOWTO)
[http://linuxselfhelp.com/howtos/Cyrillic/Cyrillic-HOWTO.html](http://linuxselfhelp.com/howtos/Cyrillic/Cyrillic-HOWTO.html)

look at Raymonds posting:
[http://www.linuxforum.com/forums/index.php?showtopic=117965&st=0](http://www.linuxforum.com/forums/index.php?showtopic=117965&st=0)
But keep off hoary as long as possible

---

### Post by Programmer on 2004-12-26
Thanks, you helped me a lot.

---

### Post by Artiom on 2004-12-28
> I think keymaps can be switched in GNOME with a panel-applet - haven't done yet. 
right click on panel -> Add to panel -> Keyboard indicator -> right click on the indicator -> Open keyboard preferances -> Layots -> Add Israeli and Russian

PS
could you configure system so it can see hebrew and russian file names together?

---

