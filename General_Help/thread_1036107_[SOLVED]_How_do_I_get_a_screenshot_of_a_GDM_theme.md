---
title: "[SOLVED] How do I get a screenshot of a GDM theme?"
date: 2009-01-10
forum: General Help
---

### Post by fredbird67 on 2009-01-10
I've got a new GTK and Metacity theme I've created, plus I've also done a modification of two existing GDM greeter themes on Ubuntu-Art.org and they're working fine.  However, I have a dumb question:  I cannot figure out how to make a screenshot of the GDM greeter/login screen.

I tried using the "Take Screenshot", setting it for 30 seconds, and then immediately logging out in hopes that it would grab a screenshot of the login screen, but that didn't seem to do the trick.  Any ideas?

Thanx in advance,
Fred in St. Louis, MO USA

---

### Post by Ivo Moelans on 2009-01-10
This only works if you have *Xnest* installed (if not: it is in the repositories) and *gdmthemetester* (this should be part of the gdm package). You can test if you have them by typing these lines (one by one) in a terminal:

```
whereis Xnest
whereis gdmthemetester
```

If both are there you are good to go

In terminal type

```
gdmthemetester xdmcp <NameOfGdmTheme>
```

This will produce a window of which you can take a screenshot. Drawback: personalized user icons are replaced by a default icon.

Hope this helps.

Edit:

You will have to take a screenshot with *Print Scrn* of the whole screen. It seems you can't use *Alt = Print Scrn* to take a screenshot from an Xnest window (but they are working on it)

---

### Post by fredbird67 on 2009-01-10
Thanx!  Did the trick, although the screenshot tool didn't seem to work when setting it to doing a screenshot of just the active window, so I went with the fullscreen setting on it and cropped out everything I didn't need in the GIMP.  Now I'm ready to post all my stuff online! :-)

---

### Post by Ivo Moelans on 2009-01-10
You're welcome.
The screenshot thing I remembered later and placed in an edit. Apparently you had already read my post before that.

---

