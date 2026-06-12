---
title: "Can I remove titles from desktop icons?"
date: 2008-09-25
forum: Desktop Environments
---

### Post by arbulus on 2008-09-25
Does anyone know if it is possible to configure icons on the desktop to have no title?  I just want the icon, I don't want the name of the app underneath the icon.  I tried just making the name a space, but that doesn't work.  And I tried creating launchers with no title at all and it won't allow it.  Is there maybe some settings in gconf editor that can change this behaviour?  

I use GNOME, btw.

---

### Post by Thingymebob on 2008-09-25
I don't think so,
The [Desktop Entry Specification]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html") requires a name value. so it looks like the best you can do is set the name to a small character such as a period (.)

As the desktop is drawn by Nautilus any changes you make would probably effect how the file browser behaves as well

---

### Post by Kinetic Being on 2008-09-25
This *is* possible, with some special name. I'm not sure what it is, but try using the forum search, I know I saw it here before...

---

### Post by Thingymebob on 2008-09-26
OK just hit this thread which may work, although I haven't tried it [http://ubuntuforums.org/showthread.php?t=872418&highlight=desktop+icon]("http://ubuntuforums.org/showthread.php?t=872418&highlight=desktop+icon")

---

### Post by Thingymebob on 2008-09-27
Just tried it, and it worked
*open character map (Applications>Accessories>Character Map)
*search for a non displaying character (ctrl+F and type U+FE0D)
*Copy it
*Open the launcher and in the name field paste it (ctrl+v)

---

