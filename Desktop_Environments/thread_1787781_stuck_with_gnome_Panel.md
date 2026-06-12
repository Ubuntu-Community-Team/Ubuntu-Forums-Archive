---
title: "stuck with gnome Panel"
date: 2011-06-21
forum: Desktop Environments
---

### Post by Jimstehrman on 2011-06-21
Hey all,

I'm stuck with gnome panel running behind my unity interface. I tried getting rid of it with gconf editor, but it isn't a part of my session anymore (???). So it's just kind of running over top of the top Unity taskbar.

Any thoughts?

Thanks!

---

### Post by Frogs Hair on 2011-06-21
You could try ```
killall gnome-panel
``` It is possible to start the Gnome Panel in unity via the terminal , but I have never heard of it starting by its self until now.

---

### Post by Krytarik on 2011-06-21
It seems like you are running the "Ubuntu Classic" session, and have the "Ubuntu Unity Plugin" enabled in "CompizConfig Settings Manager", or even the profile "Unity" selected in "Preferences" (lower left).

Greetings.

---

### Post by Jimstehrman on 2011-06-23
Yea, I have unity enabled under compiz, is there a more streamlined way to do this?

---

### Post by Krytarik on 2011-06-23
> **Jimstehrman said:**
> Yea, I have unity enabled under compiz, is there a more streamlined way to do this?
Obviously, set "Unity" as the profile in the Unity session, with the "Ubuntu Unity Plugin" enabled; and "Default" in classic Gnome, with those plugin disabled. ;-)

---

