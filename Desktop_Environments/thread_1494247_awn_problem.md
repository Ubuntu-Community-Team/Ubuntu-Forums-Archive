---
title: "awn problem"
date: 2010-05-26
forum: Desktop Environments
---

### Post by edo vulcano on 2010-05-26
i have a problem with my awn on ubuntu 10.
when i run awn,i riceive the following reponse:
edoardo@edoardo-desktop:~$ avant-window-navigator
Screen is composited
** (avant-window-navigator:5768): DEBUG: Updating gtk theme colours
** (avant-window-navigator:5768): DEBUG: Updating dialog colours
** (avant-window-navigator:5768): DEBUG: Spawned awn-applet[5769] for "quick-prefs.desktop", UID: 1, XID: 62914604
** (avant-window-navigator:5768): DEBUG: Spawned awn-applet[5771] for "taskmanager.desktop", UID: 1272795050, XID: 62914605

(awn-applet:5771): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed.


is on  the desktop but is transparent and does not respond

---

### Post by edo vulcano on 2010-05-28
help !
p.s. i use gnome

---

### Post by edo vulcano on 2010-05-30
i wanna rock

---

### Post by SnickerSnack on 2010-05-30
Hmmmm, by googling it seems that no one else has ever encountered this error.  I only found another thread made by you.

Have you tried running it as it is now installed in a different desktop environment, say xfce or kde (is kde compositing?)?

Did you install via apt or from source or is this a binary?

Which version of awn is this?

Are you running 10.04 beta/alpha or the stable release?  Is your installation of 10.04 an upgrade from 9.10?  I ask because it seems that many problems which arise after upgrading from 9.10 do not exist on a clean install.  I am still using 9.10, so I can't even say for sure whether awn works in 10.04.

Edit: Also, have you tried turning off all of Compiz' effects (but leaving compiz "on")?  It's possible that something in Compiz interferes with awn.

---

### Post by edo vulcano on 2010-05-30
I  solved.
I  changed settings
in system>preference>awn settings.


now I can interact with awn
i think was a bug.

---

