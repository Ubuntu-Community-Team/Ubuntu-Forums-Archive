---
title: "Dual Desktop-- Programs Autostart in Only One Enviroment?"
date: 2009-03-07
forum: Desktop Environments
---

### Post by vgrisham on 2009-03-07
So, I have just added the KDE desktop to my rig and I'm wondering if there is a way to only have certain applications launch automatically in gnome only (not in KDE). For instance, in gnome, I use the Avant Window Navigator dock, but it doesn't really work well in KDE. Is there any way I can have AWN only boot in my Gnome session?

---

### Post by sakkabrodir on 2009-07-20
> **vgrisham said:**
> So, I have just added the KDE desktop to my rig and I'm wondering if there is a way to only have certain applications launch automatically in gnome only (not in KDE). For instance, in gnome, I use the Avant Window Navigator dock, but it doesn't really work well in KDE. Is there any way I can have AWN only boot in my Gnome session?

I've got the same problem - have you found any solution jet?

---

### Post by vgrisham on 2009-07-20
> **sakkabrodir said:**
> I've got the same problem - have you found any solution jet?
 
No, I gave up. I'd like to use Windows7, er, KDE I mean, but I don't want to mess with shutting down my gnome stuff every session.

---

### Post by Zorael on 2009-07-20
Well, KDE has a KDE-specific autostart directory (~/.kde/Autostart). Perhaps there's a similar one in ~/.gnome2, or wherever?

---

### Post by pritamps on 2009-07-20
Each of your autostart files can be found in ~/.config 

Just add this line

```
ONLYSHOWIN=GNOME;
```

and it will start only in Gnome...

---

