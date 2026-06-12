---
title: "gnome shutdown no longer works"
date: 2009-01-06
forum: General Help
---

### Post by SunnyRabbiera on 2009-01-06
Alright recently I decided what the heck and update to ibex on my spare machine, but I have a problem.
My gnome shutdown button no longer works, period.
I click the icon, tell gnome to shut down my computer...
Nothing happens.
To shut down now I only have two options, hard shutdown (that I hate doing) and going though the mess of logging out and shutting down from the GDM screen.
I had this issue before with hardy, but I thought maybe the update will help it... guessed wrong huh?

---

### Post by tuxxy on 2009-01-06
Have you disabled any sessions, specifically power management daemon as this will prevent the shutdown menu to function. 

Also dont keep doing hard shutdowns! until you get a fix for the GUI method open a terminal and either type this to shutdown

```
sudo shutdown -h now
```

or to reboot you could use

```
sudo shutdown -r now
```

---

### Post by SunnyRabbiera on 2009-01-06
Yeh its strange, I think I got it working again though :D
I will report if it happens again.

---

