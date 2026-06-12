---
title: "lag when drag selecting"
date: 2005-10-14
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-10-14
when i use kubuntu and i multi select icons with my mouse (click and drag) the mouse movement lags ALOT, same goes when i multi select icons in konqueror....is there any way to fix this?



also how do i put a link to my mounted drives on my desktop like gnome does?

one more thing, when i put my usb pen drive into my comp, kubuntu doesnt auto mount it, how do i fix that?

---

### Post by Estariel on 2005-10-15
> 
when i use kubuntu and i multi select icons with my mouse (click and drag) the mouse movement lags ALOT, same goes when i multi select icons in konqueror....is there any way to fix this?

This is caused by the nice opaque effect which now fills the selection frame. Since this effect is an ugly hack (true transparency isn't stable yet) one experiences this lag. This is not part of vanilla kde, and I really don't understand why the developers decided to put this into kubuntu.

As for activating real transparency, I wouldn't advise it. The last time I tried (about 3 months ago) one couldn't work for longer than an hour before X would freeze.
 
 > 
 also how do i put a link to my mounted drives on my desktop like gnome does?
 
 one more thing, when i put my usb pen drive into my comp, kubuntu doesnt auto mount it, how do i fix that?

This is a known bug; kde doesn't know about HAL and thus won't talk to it. There should be a fix for this soon. If you don't want to wait, you can upgrade to kde 3.5 beta1 (but this is a beta, so beware) which doesn't have these problems. There is a thread here somewhere on how to upgrade. I've been running it for a day now, and it is reasonably stable.

---

### Post by DarkManX4lf on 2005-10-15
thanks i think i'll stick with gnome for now until these problems are solved.

---

### Post by Navyblue on 2005-10-24
Is there a way to disable it?

On other distro that doesn't use this I can feel snappier interface (even on AMD64 machine). And IMO, it doesn't even look better.

---

### Post by beefsprocket on 2005-10-24
Indeed, Mandriva 2006 and Suse 10.0 have no lag when selecting icons. I've tried both KDE3.5 beta1 and beta2 both with the same lag resulting.

Thoughts?

---

