---
title: "Keyboard locks on KDE Start"
date: 2011-03-27
forum: Desktop Environments
---

### Post by H4rm0ny on 2011-03-27
I'm having serious problems here. Yesterday, all of a sudden, the keyboard on my Kubuntu 10.10 system locked completely. Nothing did nothing and the Num Lock, Caps Lock et al. are frozen. Mouse and mouse buttons are fine.

Everytime I reboot, it's all okay at the BIOS stage, at the GRUB loading stage, and at the login stage. It's only after I login, and part way through the KDE splash screen (where it's starting all its services) that it suddenly freezes. (I know this because I'm tapping the Num Lock on and off while KDE starts).

I've tried rebooting into a previous kernel - no difference. I don't recall installing anything new recently and I wasn't doing anything odd at the time it happened.

Really need to fix this urgently as have to get some work done. Don't know whether to start re-installing O/S right now (and it will take ages to back everything up first), or wait until shops are open and buy a new keyboard to try. Current keyboard is PS/2. Don't know if using a USB one might make a difference, hence might buy one later.

---

### Post by H4rm0ny on 2011-03-27
Further information:

By cunning use of the Insert Special Character option in KWord, I have managed to enter my password and "Gnome Desktop" and installed said environment. Keyboard works fine in Gnome.

Want to know something especially weird? The Virtual Keyboard application which lets you type using the mouse on an onscreen keyboard... It does nothing in KDE, but does in Gnome. Whatever is locking my keyboard in KDE actually affects a virtual keyboard application!

Thanks for any replies.

H.

---

### Post by kio_http on 2011-04-02
I have a strong feeling this has something to do with kwin.

Try ```
metacity --replace
``` and see if the keyboard works.

---

