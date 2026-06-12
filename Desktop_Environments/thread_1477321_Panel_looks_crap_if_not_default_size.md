---
title: "Panel looks crap if not default size"
date: 2010-05-08
forum: Desktop Environments
---

### Post by Paresh on 2010-05-08
I usually change the default bottom panel settings so that I have it on the right hand edge of the screen, 100 pixels wide and auto hide checked.

Until now, this has been fine, but with ubuntu 10.4, it has an awful banded look.

So, I tried using a solid colour and a custom background image and although this improves matters, there is still a banded section at the top that should not be there.

When you have a few apps running, the taskbar shows the active app normally, but the background apps are banded again.

Is there a way to fix this?  It also makes the apps difficult to read.

---

### Post by jerrrys on 2010-05-08
any chance of a screenshot?

---

### Post by Paresh on 2010-05-09
Sorry, I got called away.

**Screenshot1** is my usual setting (right hand side, autohide & 100 pixels wide).
**Screenshot2** is set with a solid colour background.
**Screenshot3** is set with a background image.
**Screenshot4** shows the effect with some apps running.

As you can see, when the solid colour or image is used, there is still a section of the panel that has the banding effect near the top and behind the wastebin.

I actually find the banding behind the text of the apps distracting and difficult to read.

---

### Post by howefield on 2010-05-09
Not exactly a fix, but you might improve the look by playing with the transparency setting of the panel.

---

### Post by P4man on 2010-05-09
gnome panels are really poor if used vertically. I would suggest you look in to another dock like docky or avant and put that on the side.

---

### Post by Paresh on 2010-05-09
> **howefield said:**
> Not exactly a fix, but you might improve the look by playing with the transparency setting of the panel.

Transparency only affects the solid colour part, and has no effect on the banded part that is causing the problem.

---

### Post by jerrrys on 2010-05-09
not sure how it will work on your custom desktop, but **gnome color chooser** may be the answer.  its in synaptic package manager.

---

### Post by dagrump on 2010-05-09
It's the default theme that causes that, just try transparency on the top panel. Some sections won't be transparent.
Only option is change themes would be my guess. That's probably not much help, but I tried it on my box w/o the default theme & no banding here.

---

### Post by jimrew on 2010-05-09
This fixed it for me.

[http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

Hope it helps.

---

### Post by dagrump on 2010-05-09
@jimrew, good find there, I might try the default theme again.

---

### Post by Paresh on 2010-05-09
> **jimrew said:**
> This fixed it for me.

[http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

Hope it helps.

That's done the trick  Many Tanks.

---

