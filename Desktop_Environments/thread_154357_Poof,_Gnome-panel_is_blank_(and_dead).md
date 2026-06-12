---
title: "Poof, Gnome-panel is blank (and dead)"
date: 2006-04-02
forum: Desktop Environments
---

### Post by maruchan on 2006-04-02
One day I lost everything that was showing on Gnome-panel. I don't really know how. I cannot right-click it to add the old items back. Apps that are running don't show in the taskbar. I just see two long, blank bars on my screen now. It seems everything other than Gnome-panel works fine though (Alt-F2 doesn't work, is that part of the panel?). Here's what I've tried to fix this, to no avail so far:

-Killall gnome-panel (restarts with same stuck/blank situation)
-Delete .gconf2 -> apps -> panel folder and reboot (same result as before, problem persists)

Can anyone tell me what I should try next? Did I miss a config folder that I should have deleted? Thanks.

---

### Post by manicka on 2006-04-02
Do you remember what the last thing was that you added to the panel?

---

### Post by maruchan on 2006-04-03
Hmm...I added a drawer a while ago, and it seemed it didn't enjoy that experience very much.

Also, I recall now that this crashing problem started around the time when I changed the theme. Maybe I should try changing the theme to something else!

---

### Post by manicka on 2006-04-03
Yes, go back to the default theme and see what happens

---

### Post by maruchan on 2006-04-03
I will try that, thanks for your help :)

---

### Post by manicka on 2006-04-03
without a panel running you'll need to run the command

```
gnome-theme-manager
```

in a terminal

---

### Post by manicka on 2006-04-03
Another thought, I also had a problem once with the deskbar applet in breezy that caused the same result. I had to remove it with synaptic (gksudo synaptic) and restart gnome  before I could get things working again.

---

