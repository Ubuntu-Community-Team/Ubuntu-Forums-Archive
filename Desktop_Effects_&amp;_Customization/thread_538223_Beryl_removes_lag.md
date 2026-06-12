---
title: "Beryl removes lag?"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by ZeldaFan on 2007-08-29
One peculiar thing I have noticed with installing beryl is that when dragging windows, there is no lag. For example, without beryl, and just using metacity and gtk, if you were two drag a firefox window across an openoffice Writer window, you would notic some lag resulting from the dragging. However, with beryl that lag is eliminated, and dragging seems much more crisp. Of course scrolling is noticeably slower with beryl than without it, but I couldn't help wondering why beryl's dragging is much more crisp. Is there anyway to achieve that kind of behavior without having to fully install beryl?

---

### Post by Steveway on 2007-08-29
That is what compositing managers are for.
Your Windows are textures that are moved and drawn by your graphicscard, and for most cards this is an easy task and it will be smooth.
If you don't use a compositing manager then your CPU draws the screen and if you move a window it has to repaint it all the time.
You can use a lighter compositing manager like xcompmngr or XFCE's built in Compositing manager to archive the same effect.

---

### Post by ZeldaFan on 2007-08-29
Well I use gnome so do I just install xcompmngr? Also I was wondering, as this was my only really useful feature in beryl, as to whether or not there are lighter programs that give me scaling functionality as well. You know like when you drag your mouse to the upper right hand corner and you see all the windows scaled.

---

### Post by Steveway on 2007-08-29
Nope that is a Beryl/Compiz feature.
But if you want that, then you could continue using Beryl and just turn of all unnecessary features.

---

### Post by ZeldaFan on 2007-08-29
how do i install xcompmgr? apparently I can't just apt-get install it

---

### Post by Steveway on 2007-08-29
Do you have the multiverse and universe repos enabled?
I can't say for sure but I have it here in my repos, but I run Gutsy.
If you can't find it in Synaptic then search on the forum, there are for sure howtos for it.

---

### Post by ZeldaFan on 2007-08-29
oh yea, it was because I just copied and pasted the name from your post. The correct name is xcompmgr, but you wrote xcompmngr. That's probably why apt-get wasn't working. Either way I just got it from synaptic. I ran it through alt +F2 and I think its working cause I experience much better window dragging. But is there any tray icon or something similar to change its settings?

---

### Post by Steveway on 2007-08-29
Not that I know of.
Afaik it only adds basic compositing features.
Sorry for the typo. ^^

---

### Post by ZeldaFan on 2007-08-29
Well, either way, thanks so much. I have never needed beryl's extra features, and I would've never installed it without the lag I was experiencing before. This was the exact solution I was looking for, I just never knew I needed a compositing manager to get what I was looking for.

---

