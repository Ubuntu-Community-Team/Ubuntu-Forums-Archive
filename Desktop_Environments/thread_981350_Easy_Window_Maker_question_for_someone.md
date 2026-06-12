---
title: "Easy Window Maker question for someone"
date: 2008-11-13
forum: Desktop Environments
---

### Post by TNAFan on 2008-11-13
I use the GnuStep destkop, and I have come up with a real quick question for someone that knows Window Maker.  I can't seem to figure out what the E on the title bar is used for.  I push it, and it turns white, I release it, and it goes back to normal, but it doesn't seem to do anything.  Can anyone tell me what it is for?  Thanks.

---

### Post by TNAFan on 2008-11-14
Come on, there has gotta be someone out there who knows what the E is for.  Anyone?

---

### Post by Nergui on 2009-01-12
Don't know if you're still around or still interested, but the 'E' just stands for English, and the button is just for switching keyboard layouts. To use it, you have to put the 2-letter code for your alternate layout(s) (e.g. 'fr' for French) next to 'en' in the keyboard section of your xorg.conf. Then you can either hit the button to switch back and forth (one window at a time), or set a keyboard shortcut. I use it all the time.

Unfortunately, Ubuntu has changed the way keyboard layouts are handled in Intrepid, so this no longer works. It is managed by HAL now, but the current setup pretty much requires you to be running GNOME/KDE/XFCE. I'm sure there's a way to fix it, but I haven't gotten around to looking (it would involve messing around with XML files). A workaround is just to load kxkb (or whatever the equivalent is in GNOME) and close it again, and the E will work fine again for the duration of your session.

---

