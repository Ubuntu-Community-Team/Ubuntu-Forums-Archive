---
title: "Background blue for a second after login, should be gray?"
date: 2007-01-20
forum: Desktop Environments
---

### Post by featherking on 2007-01-20
I recently changed my login theme and splash image to a more gray color and ive noticed that after i login and after the splash image but before the desktop icons appear, the screen will change to a dark blue and then my desktop background appears and my gnome panels and the icons.

I have tried searching everywhere for where this blue could be coming from. Ive set my login color to gray and the desktop background color to gray, i edited /etc/gdm/gdm.conf and made sure that was set to gray. But somewhere i still get this blue?

Any ideas where i can track it down?

---

### Post by bapoumba on 2007-01-20
Hi,
probably the GDM login screen background ;)
You can change it in GDM login theme.

---

### Post by mcduck on 2007-01-20
what background color do you have configured with the wallpaper you are using? this color will show before the actual wallpaper image is loaded..

---

### Post by featherking on 2007-01-20
> **bapoumba said:**
> Hi,
probably the GDM login screen background ;)
You can change it in GDM login theme.

If you are refering to System > Admin > Login Window, i have changed this color to gray already. I even changed it to bright red to test and see if it was working. This resulted in a bright red screen during the splash screen and then just before my desktop appears, it will flash blue for about one second???

> what background color do you have configured with the wallpaper you are using? this color will show before the actual wallpaper image is loaded..


I also set this to bright red to test, but the bright red never shows up? i suspect that that setting is not taking affect. Any ideas on where i can change or reset that value?

---

### Post by featherking on 2007-01-20
is there some way i can delete just my desktop settings or revert them to default in an effort to remove this color? i found a reference to the color #1471CA in /etc/gdm/gdm.conf-custom and i renamed the file but still the blue screen appears just before the desktop background. I am now running a search for all files containing the phrase "#1471CA" to see if there are any references to it on my computer, so far only that file in /etc/gdm has come up...

Can i somehow reconfigure that and not mess up my entire desktop?

---

### Post by bapoumba on 2007-01-22
Hi,
should be in <your_gdm_theme>.xml, at least that's were I changed it (to a grey one too ;))

---

