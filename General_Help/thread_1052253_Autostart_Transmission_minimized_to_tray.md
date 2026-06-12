---
title: "Autostart Transmission minimized to tray?"
date: 2009-01-27
forum: General Help
---

### Post by Bllz on 2009-01-27
Hello!

I've managed to get transmission to start upon login via "Sessions" with the command "transmission %F" (I got it from the main menu).

I was wondering, is it possible to get it to autostart minimized in the task bar?

Thanks a bunch,
Bllz

---

### Post by Bllz on 2009-01-28
BUMP


... Anyone?

---

### Post by kholsheimer on 2009-02-23
Have you tried alltray? Here's what I use. If you haven't installed alltray yet:
```
sudo apt-get install alltray
``` then add a new entry in **System > Preferences > Sessions**. Name it Transmission or whatever and put in the Command box:
```
alltray -na -nt transmission
``` the -nt and -na options will respectively prevent alltray from putting a second icon in the tray and putting "... (Alltray)" in the window title. 

There are two catches to this ad hoc solution. One is that I believe that altray doesn't really work well with compiz (I don't use compiz myself, so I'm not sure). The other is that it takes three clicks on the Transmission icon for it to pop up for the first time.

Hope that works for you.

---

### Post by makisupa123 on 2009-02-23
AFAIK transmission already has an option for a tray icon.  Look at the preferences and make sure its selected.  

Secondly, add an item to your session to start transmission (there is already a start minimize option).

```
transmission -m
```

Alltray is not necessary in this instance (although it can be handy in other cases)

EDIT:  I see that you already have a session item for this.  Just add the "-m" flag.

--Mak

---

### Post by kholsheimer on 2009-03-05
Thanks Mak, thats a lot easier! Though I can't find the "start in tray" option within the gui.

kris

---

