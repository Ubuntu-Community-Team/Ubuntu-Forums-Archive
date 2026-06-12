---
title: "Modem lights applet in KDE?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by blastus on 2005-10-27
Hi. I'm looking for an applet that I can put on my KDE panel that is similar to the modem lights applet in GNOME. But I need a brighter color like yellow or something when the in/out lights are on. Also, if it can tell if ppp0 is active, just like the modem lights applet in GNOME does, that would be super. :)

---

### Post by landotter on 2005-10-27
You can have the dialer "kppp" dock into the panel's notification area when connected. I don't remember if you can change the colors though. I dont' have KDE on this box right now, or I'd give you details. :P Used it for a couple years--works great. :D

---

### Post by Takis on 2005-10-27
Try KNetStats, it's really good (and should be able to work on any type of network connection!): [http://knetstats.sourceforge.net/](http://knetstats.sourceforge.net/)

---

### Post by jeremy on 2005-10-28
I use knemo (from the repos).

---

### Post by blastus on 2005-10-30
Thanks everyone for those tips! I saw the kppp "dock into panel" option as landotter pointed out and it works like a charm. I will check out knetstats and knemo as well.

---

### Post by odrop on 2005-10-31
If you wanted to still have brighter modem lights in kppp, it looks like you could edit the pngs in:
/usr/share/apps/kppp/pics/

and it should change to whatever color you set the activity boxes.  I havent tried it myself  but it might work.

---

### Post by blastus on 2005-10-31
[QUOTE=odrop]If you wanted to still have brighter modem lights in kppp, it looks like you could edit the pngs in:
/usr/share/apps/kppp/pics/

and it should change to whatever color you set the activity boxes.  I havent tried it myself  but it might work.[/QUOTE]

Hey that's great! I'm gonna try to replace those pngs to make the lights bigger!

---

### Post by blastus on 2005-10-31
Well I just edited the images in /usr/share/apps/kppp/pics/ and it works. Now I've got custom modem lights! :p

---

