---
title: "XFCE with Gnome Features"
date: 2006-09-29
forum: Desktop Environments
---

### Post by jperez on 2006-09-29
This has to be the weirdest thing ever to happen to me while using Ubuntu!

Well, I was fooling around with using Links to create a "My Computer", "Home Folder" and "Trashcan" on the desktop worked, but once I opened up the Trashcan icon, my desktop changed the background to the default background for Ubuntu Dapper Drake and it uses the Gnome desktop features.  Screenshots are included.

In fact, the "My XFCE", "My Home" and "Trash" icons were placed on the desktop using **gconf-editor**.  Has anyone else experienced this before?  No, I'm not looking for a solution since this is much better for me, I thought I would just share this with everyone.

Jesse~

---

### Post by Sef on 2006-09-29
I guess some-gnome must love you.

---

### Post by aysiu on 2006-09-29
Nautilus isn't just a file manager--it also manages the desktop. If you enable Nautilus, it'll "take over" XFCE's desktop.

If you don't want that to happen, you should launch it was ```
nautilus --no-desktop
```

---

### Post by Rui Pais on 2006-09-29
You are probably using xfce with nautilus instead of thunar or xffm.

Since nautilus is the app that draws the Gnome's Desktop and that behaviour is the default for nautilus you get xfce+ gnome default.

If you want to disable that option do it with gconf-editor:
app->nautilus->preferences->'show desktop' (enable/unable)

Another possibility is that you simply have gnome-settings-daemon started automatically on your xfce session.

---

### Post by jperez on 2006-09-29
Well, I don't know how it happened since when I started XFCE and it didn't start up with **nautilus**.  It happened once I opened the custom "Trashcan" icon.  Either way, **nautilus** is running very fast under XFCE.  I have no quips about it.  It was just weird is all.  Good night.

Jesse~

---

### Post by Rui Pais on 2006-09-29
> **jperez said:**
> Well, I don't know how it happened since when I started XFCE and it didn't start up with **nautilus**.  It happened once I opened the custom "Trashcan" icon.

That's because when you hit the Trash icon it launched nautilus and not the xfce default file manager. So Nautilus started with the default options, without the flag that aysiu mentioned (--no-desktop) and draw gnome's desktop. 

>  Either way, **nautilus** is running very fast under XFCE.  I have no quips about it.  It was just weird is all.  Good night.
Thats because you are not running gnome or even a gnome-session, that have a lot (really lot) stuff running underground, but only nautilus - a single app - with a different window view, the special  folder 'desktop' opened in fullscreen no borders or close buttons. 

It's fast and allow desktop icons much easier and nicer the xfce does, but have the downsize that bring back the useless mouse menu (for the right button) from gnome instead of the full apps menu from xfce.

---

### Post by jperez on 2006-09-29
One last thing before I hit the hay,

Well, I already have the full menu in the **Applications** menu bar, so I really don't mind not having it in the right click.  Sure, it's great to have on hand, but I don't need it.  I actually found it rather annoying and **nautilus** allows me to make Launchers a LOT easier.

Jesse~

---

