---
title: "compiz in gnome fine - in KDE not so!"
date: 2010-10-27
forum: Desktop Environments
---

### Post by Krondaj on 2010-10-27
Hi I have been using ubuntu for about two weeks now with the full desktop effects such as cube rotation (using middle mouse buttin).  However, when I installed KDE that I can pick to go in at log in every time I do that I get an annoying abundance of post it notes.  I cannot seem to change the preferences to get rid of the postits and get the cube rotation

Any suggestions??

Thanks

Chris

---

### Post by Silent Warrior on 2010-10-27
Ah, a D'oh!-moment! (Cherish 'em when they're harmless...) KDE doesn't use Compiz - its window manager, KWin, has compositing of its own. Open System Settings, look for Desktop Effects (in 4.5, it should have its own module). Tweak away as you like.

I don't know what post-its you're talking about, but if it's the plasmoid-thingy it'll be as easy as unlocking the desktop-widgets, mouse-overing the post-its, and clicking the 'x'.

---

### Post by 3Miro on 2010-10-27
You could use compiz in KDE, however, it is strongly recommended that you use kniw. System Settings -> Desktop -> Desktop Effects, it has most of what compiz has and it does have a nice cube.

---

### Post by hellnest on 2010-10-27
> **Krondaj said:**
> Hi I have been using ubuntu for about two weeks now with the full desktop effects such as cube rotation (using middle mouse buttin).  However, when I installed KDE that I can pick to go in at log in every time I do that I get an annoying abundance of post it notes.  I cannot seem to change the preferences to get rid of the postits and get the cube rotation

Any suggestions??

Thanks

Chris

Lol it's fun... I can use effect in KDE but can't do anything in Gnome. At least transparency and Shade + Fade effect is working in KDE ( i'm using SIS Cursed Onboard VGA )

So here's the solution for you, for example that you running the latest KDE Version 4.5.2

```
1. Go to System Setting
2. Find Desktop Setting
3. Go to Effect section and Tick " Enabled Effect "
4. On the 3rd Tab in top, you can choose option between OpenGL and Xrender. Try to use Xrender and see if it works or not. Also in advanced section try to tick all the effects that you want to enable
```

---

