---
title: "Need help with Nitrogen 1.4"
date: 2009-02-15
forum: General Help
---

### Post by jpe.1337 on 2009-02-15
Okay, so I've downloaded, compiled, and install Nitrogen successfully. I have it set so it "sees" my wallpaper directory as well. The problem I get though with this program is I cannot set my wallpaper.

The main reason what attracted me to this program is that it as the ability to display multiple wallpaper for multi-monitor set-ups. I have a 17" CRT monitor and a 26" Samsung HDTV.

---

### Post by jpe.1337 on 2009-02-16
bump

I'll give some :popcorn: for anyone who can help... ;)

---

### Post by jpe.1337 on 2009-02-16
...

---

### Post by jpe.1337 on 2009-02-16
????

---

### Post by jpe.1337 on 2009-02-17
Again, can someone please help me...

---

### Post by m_duck on 2009-02-17
I think when you use nitrogen to set the wallpaper, it sets the root wallpaper. In GNOME, whatever sets the wallpaper (maybe nautilus) draws a new layer over the root wallpaper to draw its wallpaper on. This is why when you change the wallpaper in nitrogen, it has seemingly no effect - because GNOME's wallpaper is on top of it.

As for the actual answer of two wallpapers on two desktops I'm unsure, but the above is why nitrogen won't work.

---

### Post by jpe.1337 on 2009-02-17
Well, I'm getting somewhere. When I set the wallpaper to none on the regular Gnome wallpaper settings and then open Nitrogen, I can change the wallpaper, but as soon as I open a Nautilus window, it goes back to what it was.

---

### Post by jpe.1337 on 2009-02-17
And also, thank you for the help...now I need to figure out how to set Nitrogen as my default wallpaper manager.

---

### Post by jpe.1337 on 2009-02-17
bump

---

### Post by m_duck on 2009-02-17
I don't know about a default wallpaper manager, but adding the following to autostart on login (System -> Preferences -> Sessions) will restore the previous wallpaper ```
nitrogen --restore
```

---

### Post by jpe.1337 on 2009-02-17
Doing that makes me unable to right click on my desktop or see my files. The only way I can get it back to normal wallpaper (not controlled by Nitrogen) is if I click my trash can.

---

### Post by jpe.1337 on 2009-02-18
bump

---

### Post by jpe.1337 on 2009-02-18
Another bump

---

### Post by jpe.1337 on 2009-02-19
Yet another bump.

---

### Post by mytharak on 2009-02-25
There is an option in gconf to control whether or not nautilus will draw the background.

Open up gconf-editor and go to /apps/nautilus/preferences. Uncheck the box next to 'Show_Desktop'

Now you'll see that you can use nitrogen to set your wallpapers.

I just downloaded nitrogen, and I think it's pretty sweet. Now I can set a separate wallpaper for each screen!.

---

### Post by mytharak on 2009-02-25
You will also want to add the following to your gnome session (System -> preferences -> sessions).

```
nitrogen --restore
```

This will load your nitrogen backgrounds upon login.

---

