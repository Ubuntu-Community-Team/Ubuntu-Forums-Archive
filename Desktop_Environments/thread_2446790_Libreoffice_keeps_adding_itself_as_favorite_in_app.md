---
title: "Libreoffice keeps adding itself as favorite in application menu"
date: 2020-07-06
forum: Desktop Environments
---

### Post by scottbomb on 2020-07-06
This is driving me bananas. I thought it was up the USER, not the SOFTWARE to decide if the software is going to be considered one of the user's "Favorites". I use the alternative Application Menu in KDE. The sidebar on the left is for those applications that I use often. I, the user dictates what shows up here. At least that's how it's supposed to be.

Thanks to an entry in /usr/share/libreoffice-startcenter.desktop, the icon appears there after every reboot, even after I've explicitly removed it. The only way to KEEP it gone is by deleting the file just mentioned. Sadly, it returns with every apt update procedure like a wart that just won't go away. I don't see this as a Libreoffice bug (though I am considering a switch to OpenOffice because of it), but in my opinion, NO application should be allowed to just add itself as a favorite in one's menu.

Is there a setting somewhere that locks this down or should I open a KDE bug? I'm guessing it's by design but it's downright obnoxious.

---

### Post by speartip on 2020-07-08
It is a bug that keeps cropping up that is annoying. it is a menu bug though. I now use the "Cascading Application Menu" instead, as I like it's simplicity and the LO StartCenter icon doesn't show up there. 
You could try the solution from here, & see if that works. Otherwise deleting the file you mention seems to be the best option.
[https://forum.manjaro.org/t/libre-writer-recreates-favorite-shortcut-after-every-boot/83257](https://forum.manjaro.org/t/libre-writer-recreates-favorite-shortcut-after-every-boot/83257)

---

### Post by scottbomb on 2020-07-09
Thank you for confirming. I haven't used OO in a while, I think I'll give it a spin.

---

