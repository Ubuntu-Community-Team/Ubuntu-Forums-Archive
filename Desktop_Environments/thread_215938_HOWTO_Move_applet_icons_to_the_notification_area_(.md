---
title: "HOWTO: Move applet icons to the notification area (aka system tray)"
date: 2006-07-14
forum: Desktop Environments
---

### Post by mycelo on 2006-07-14
Hi, this is my first HOWTO. I've searched everywhere for a minor annoyance that I had with Gnome panels, and after gathering bits of information throughout several threads, I finally managed to get things right. I hope it comes to be useful for someone.

My headache started when I accidentally moved my audio/volume icon/applet away from the notification area/system tray. You know, in the extreme right of the top panel, where your clock lies (and where the notification icons pop sometimes). Then I realized that I just couldn't move it back. The opposite action not always can undo things, that's life.

Ok, firstly my reaction was like "no big deal, I'll leave that icon somewhere else". But I just couldn't forget the fact that I am not able to put that icon back there! I asked some friends, and they came to the same situation. Actually they became mad at me, because now their freaking icon is "broken" too.

As far as I could learn, the notification area is itself a sub-panel that lies upon the top panel (and can stay on top of any other panel). If you move an icon out of it, it automatically shrinks to embrace the remaining icons. But since it's locked in the top panel, you can't move it and you can't drag-grow it (by moving its barely visible border/separator to the left). And if it has no empty space, you can't move an icon there as well. It does not grows back automatically. Bug?

Solution: 

Right-click the left border of the notification area. The drop-down menu that you get is about this whole sub-panel. Click on the last menu command to unlock it.

Now you're able to grow it by dragging its border to the left, so you make empty space for your icons.

Now move there whichever icon you want by unlocking (right-click) and dragging (middle-hold) each one.

Right-click each icon again and re-lock them. Optionally, drag the notification area's border to the right, squeezing any empty space that remained inside it (I think it does this automatically when you re-lock the whole notification area).

Right-click the border of the notification area and re-lock it and we are done.

Well I admit that this is such a long guide for such a futile matter, oh well.

mycelo

[EDIT] According to the poster below, the notification area isn't a panel itself, you can have icons in the right side of it which will show up like they're on top of it, since it doesn't have a visible right boundary. However, I am not sure why it slides towards the right of the screen when you move the clock and the volume applet to the left.

---

### Post by temcat on 2006-07-15
You don't move icons to the notification area, they appear and disappear from there automatically. Notification area is not a subpanel, it's just another applet. The clock applet is not inside the notification area - it's just *on the right* of it. Yes, when it's locked to the panel you should not be able to move icons past it, but so is the case with any other applet. The fact that could move your audio applet in one direction may actually point to a bug.

---

### Post by mycelo on 2006-07-17
> **temcat said:**
> You don't move icons to the notification area, they appear and disappear from there automatically. Notification area is not a subpanel, it's just another applet. The clock applet is not inside the notification area - it's just *on the right* of it. Yes, when it's locked to the panel you should not be able to move icons past it, but so is the case with any other applet. The fact that could move your audio applet in one direction may actually point to a bug.
I appreciate your clarification, I was pretty sure that I was putting things inside a sub-panel. My HOWTO is still valid though.

---

### Post by temcat on 2006-07-18
> **mycelo said:**
> I appreciate your clarification, I was pretty sure that I was putting things inside a sub-panel. My HOWTO is still valid though.

I actually wish it was a subpanel ;-)

---

### Post by Dominicus on 2006-12-09
This worked for me.  Was going insane with those icons out of order!

Thank you! Dominicus

---

### Post by 1TruthStudios on 2006-12-12
I can't find my system tray : ( Is there a way I can make a new one? I'm really sick of not having Gaim down there

Mathias

---

### Post by mcduck on 2006-12-12
right-click on the panel, select 'add to panel', find 'notification area' and drag it to your panel.

---

### Post by mgrusin on 2006-12-30
> **mcduck said:**
> right-click on the panel, select 'add to panel', find 'notification area' and drag it to your panel.

THANK YOU! :KS   I accidentally deleted that "bar" thing (I thought it was a separator, not a separate panel) and have been chasing ghosts trying to figure out how to get the icons back there (dragging .desktop icons around, reinstalling apps, etc). ](*,)

---

