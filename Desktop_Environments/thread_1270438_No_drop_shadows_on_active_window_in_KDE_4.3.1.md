---
title: "No drop shadows on active window in KDE 4.3.1"
date: 2009-09-19
forum: Desktop Environments
---

### Post by Izobalax on 2009-09-19
I am however, getting shadows on menus and inactive windows. All my active windows just have an annoying blue glow around them. How do I address this?

PC specs in my sig.

/izo\

---

### Post by kellemes on 2009-09-19
You have been at the kde settings-dialog?
Settings -> Desktop -> Desktop Effects -> All Effects -> Shadow

---

### Post by Izobalax on 2009-09-19
> **kellemes said:**
> You have been at the kde settings-dialog?
Settings -> Desktop -> Desktop Effects -> All Effects -> Shadow
Yes. Shadows are enabled. Only the active window has no shadow, just a blue glow. 

/izo\

---

### Post by Izobalax on 2009-09-25
BUMP.

/izo\

---

### Post by Giblet5 on 2009-09-25
> **Izobalax said:**
> Yes. Shadows are enabled. Only the active window has no shadow, just a blue glow. 


Did you tweak the shadow color from black to blue by any chance?

(System Settings/Desktop/Desktop Effects/All Effects/Shadows)

Changing shadow color works really well...until you change the background image to something darker.

---

### Post by Izobalax on 2009-09-25
> **Giblet5 said:**
> Did you tweak the shadow color from black to blue by any chance?

(System Settings/Desktop/Desktop Effects/All Effects/Shadows)

Changing shadow color works really well...until you change the background image to something darker.


No the shadow colour is still black, though I've changed it as an experiment - all other inactive windows/pop-ups/menus register the change in colour, but the active window is still shadowless. 

The help is appreciated. 

/izo\

---

### Post by Giblet5 on 2009-09-25
You aren't starting Emerald, I presume...

Well, you can always revert to the default as a test:

Log off.
Flip to the console via Ctrl-Alt-F1 and log in (text mode).
```
mv .kde .kde-odd
```
Log off via Ctrl-D.
Flip back to the display manager via Ctrl-Alt-F7 and log in.

That will tell you whether something is really wrong, or just misconfigured. You can always move it back.

---

### Post by Izobalax on 2009-09-25
> **Giblet5 said:**
> You aren't starting Emerald, I presume...


Nope. KDE4's Kwin with compositing on. 


> **Giblet5 said:**
> Well, you can always revert to the default as a test:

Log off.
Flip to the console via Ctrl-Alt-F1 and log in (text mode).
```
mv .kde .kde-odd
```
Log off via Ctrl-D.
Flip back to the display manager via Ctrl-Alt-F7 and log in.

That will tell you whether something is really wrong, or just misconfigured. You can always move it back.


Nice one. I shall try this and report back. 

/izo\

---

### Post by Nitronium on 2011-07-07
I know it's an old thread, but this was really annoying me too. It's nothing to do with compositing settings (but seems to only happen when compositing is enabled).

I fixed it by going into the KDE System Settings > Workspace Appearance > click Configure Decoration and disable the shadows and active window glow.

That gets rid of them, trouble is, the windows still open a few mill up from the task bar, leaving a gap for the non-existent shadow. Would love to know how to stop that.

I'm in KDE 4.6.2 btw.

Ta!

---

### Post by ankspo71 on 2011-07-12
Hi,
Have you tried logging out and then logging back into KDE again? Sometimes this step is needed for some desktop settings to get applied correctly.

---

