---
title: "Missing settings in new Nautilus?"
date: 2012-11-15
forum: Desktop Environments
---

### Post by Ev1L on 2012-11-15
Hi,
just upgraded to Quantal and using Gnome Shell.
I am trying to figure if I am missing something or they really cut the balls of Nautilus.

1 - where is "open in new window"?
2 - where is the bottom status bar with free space of current mount?
3 - how can I sort files and folders in a meaningful way? (sort by name, first folders then files)

---

### Post by Ev1L on 2012-11-15
found answer to point 3: click on files on top left near activities and select properties.
there are some settings there, but still cannot find anything useful for first 2 questions

---

### Post by diesch on 2012-11-15
I'm using 12.10 with Unity but that shouldn't make any difference

[LIST]
[*]"Open in new window" is in the "File" menu and the context menu
[*]You can enable the status bar using "Statusbar" in the "View" menu
[/LIST]

---

### Post by Ev1L on 2012-11-15
unfortunately it makes all the difference :)
under files there is only "new window", which opens Home. and it is neither in context menu right clicking on folders.
and there is no View menu, at least none with status bar that i can find.

i also noticed that they removed hh:mm from modified column. i think i will have to search for an alternative, which is extremely disappointing. i still miss gnome classic...

---

### Post by diesch on 2012-11-15
Are you using any PPA or another unofficial package source for Gnome? What does
```
apt-cache policy nautilus
```
print?

---

### Post by Ev1L on 2012-11-15
yes, gnome3-team.
did they update nautilus by removing features? :D

---

### Post by diesch on 2012-11-15
Yes, GNOME removed some features from Nautilus in GNOME 3.6. Which is why Ubuntu ships Nautilus 3.4. But I guess your PPA got you Nautilus 3.6

---

### Post by Ev1L on 2012-11-15
i think so, then i am right to blame gnome once again after leaving classic.
for now pcmanfm seems to do the work even if it looks a bit rough.

---

