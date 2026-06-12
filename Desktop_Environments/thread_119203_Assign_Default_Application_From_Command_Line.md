---
title: "Assign Default Application From Command Line"
date: 2006-01-18
forum: Desktop Environments
---

### Post by dragonfyre13 on 2006-01-18
OK, I'm making a script file for mass deployment of an exact setup. I'm missing three abilities at the commandline level to put in the script.

1. Adding things to start-up
2. Adding applets to the top panel
3. Assigning default applications to file extentions.

I haven't delved to deep into 1 or two, though I expect 2 is quite difficult, whereas 1 is quite simple. Luckily, 2 is not neccesarily needed.

Where I run into major trouble is 3. I REALLY need to do this, as the common grunt at work can't even right click half the time, let alone know how to set the default application.

I just need to be able to set the default application in nautilus to something (IE. avi files should default to VLC, not totem) and I need to do it in a script.

Help? Please?

---

### Post by bernardfrancois on 2006-01-20
You'll have to be editing configuration files, I'm almost sure of. Like that you'll be able to do all of these three things. 

I dunno where to find them, so I did a little search for the panel thing...

```

# find ~/.gnome* | grep panel
.gnome2/panel2.d
.gnome2/panel2.d/default
.gnome2/panel2.d/default/launchers

```

I guess you'll have to look in one of those directories. Let me know (by a reply here) if it worked out, and how you did it.

---

### Post by dragonfyre13 on 2006-01-20
I'll try it out.

---

