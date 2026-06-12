---
title: "Compiz keyboard shortcuts"
date: 2006-06-22
forum: Desktop Environments
---

### Post by m4rqz on 2006-06-22
Hello everyone

I've successfully set up xgl/compiz and everything works perfectly (including swedish keyboard layout), everything but this: No compiz/window manager related keyboard shortcuts work, so, no alt-tab window switching or alt-F1 menu or alt-F2 run dialog... 

Anyone with similar problems?

/Markus

EDIT: forgot to mention: all in-app shortcuts work.. like ctrl-c, ctrl-v etc.

---

### Post by ashrack on 2006-06-22
Try with gset-compiz, it's in quinn's repo.

With this program U will be able to input your shortcuts

---

### Post by m4rqz on 2006-06-26
[QUOTE=ashrack]Try with gset-compiz, it's in quinn's repo.

With this program U will be able to input your shortcuts[/QUOTE]

All shortcuts are configured, they just don't work :(

---

### Post by PuleX on 2006-06-26
When I first installed XGL/Compiz the keyboard shortcuts didn't work either, fi I remember it correctly. Changing my Keyboard layout under System > Preferences > Keyboard (to the 105 Intl?) fixed that. (not sure, I am not at home right now so I can't check)

---

### Post by art on 2006-06-26
Or add xmodmap /usr/share/xmodmap/xmodmap."your contry" to System->Prefernces->Session->Startup 
That fixed it for me...

---

### Post by m4rqz on 2006-06-27
Thanks, I'll try when I get off work. 

Cheers

---

### Post by m4rqz on 2006-06-28
[QUOTE=PuleX]When I first installed XGL/Compiz the keyboard shortcuts didn't work either, fi I remember it correctly. Changing my Keyboard layout under System > Preferences > Keyboard (to the 105 Intl?) fixed that. (not sure, I am not at home right now so I can't check)[/QUOTE]

For the record: This did the trick! Thanks!!

---

