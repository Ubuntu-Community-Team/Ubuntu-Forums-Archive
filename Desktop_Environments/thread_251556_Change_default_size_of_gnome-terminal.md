---
title: "Change default size of gnome-terminal?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by DC@DR on 2006-09-05
How could I change the default height and width of gnome-terminal so it can start up with the desired size everytime I launch the app? :confused:

---

### Post by ayoli on 2006-09-05
create a launcher (or edit menu entry with alacarte) that launches gnome term like this:
```
gnome-terminal --geometry 420x64
```
replace values by yours.

---

### Post by aysiu on 2006-09-05
I never knew that--cool!

---

### Post by DC@DR on 2006-09-05
Great, thanks for the fast response, ayoli :)

---

### Post by ayoli on 2006-09-05
glad that helps :)
actually i use alltray which allow to remove borders and have a launcher which looks like taht:
```
alltray --borderless --show "gnome-terminal --window-with-profile=Default --geometry=102x25+312+12
```

---

### Post by syn4k on 2008-05-05
-bash: gnome-terminal: command not found
It seems that if you paste this command into a shortcut, it works but not if you paste it into your terminal. At least, not here on my copy of Ubuntu. 

It would be nice to know where the properties command is stored though so I could just vim a file and edit that way.

---

