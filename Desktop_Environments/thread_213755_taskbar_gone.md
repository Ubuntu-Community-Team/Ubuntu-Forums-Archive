---
title: "taskbar gone"
date: 2006-07-11
forum: Desktop Environments
---

### Post by weissnich on 2006-07-11
I use Xubuntu (Xfce4) and my taskbar is gone,
how do I get it back?
The 'xftaskbar' command doesn´t bring it back,
any suggestions?

---

### Post by weissnich on 2006-07-11
If I go into the settings manager and
click on 'panel', it won't show up.
I need to work with the computer now,
can anybody help please???

---

### Post by aysiu on 2006-07-11
Have you run the command *nautilus* recently? How did the taskbar disappear? That may give us a clue as to how to get it back? Did you accidentally delete it?

---

### Post by weissnich on 2006-07-11
Hi,
thanks for your answer,
I don´t have nautilus, I have thunar which comes with Xubuntu,
I don´t have added any new programs recently, so I really don´t know what could have caused this :(
I just have plain Xubuntu with OpenOffice.org, Inkscape and Scribus,
no additional programs, no Nautilus, nada.

---

### Post by aysiu on 2006-07-11
Okay. That makes it more of a mystery. I just asked about Nautilus because sometimes people run that command in XFCE and it kind of takes over.

You said you ran ```
xftaskbar
``` Have you tried ```
xftaskbar4
```?

---

### Post by Tamihania on 2006-07-11
I hope it will help...Have you tried to run:

> xfce4-panel 
?
I am simply not sure if you need panel or taskbar...Sorry if I misunderstood you.:-k

tami

---

### Post by aysiu on 2006-07-11
If you're in the terminal and type ```
xf
``` and hit the **Tab** button twice instead of hitting **Enter**, you'll see all the commands that begin with *xf*.

---

### Post by weissnich on 2006-07-11
Hey, thanks!!

I needed the panel, by the way, what is the taskbar?
(my English is not so good it seems ;))
How can I get the panel to stay? if I use the command in the terminal,
the panel disappears again if I close the terminal.

---

### Post by aysiu on 2006-07-11
Alt-F2 and then the panel command.

The taskbar is the window list of what windows and applications are open, I think.

---

### Post by Tamihania on 2006-07-11
alt+F2 
and then: 
xfce4-panel

BTW:Your English is very good - taskbar=part of the panel showing tasks... ;)

Enjoy,
tami

---

### Post by weissnich on 2006-07-11
That worked, however,
I am not able to log out/reboot or shutdown from the panel, I can only shutdown the panel itself.

---

### Post by weissnich on 2006-07-11
If I reboot the panel is gone again,
what can I do???
This is really strange...

---

### Post by Tamihania on 2006-07-12
...sorry to be a bit late on that - I have to sleep sometimes.. ;)

Anyway - I had a similiar issue some time ago and AFAIR I removed the closing panel applet from the panel and then Ive added the right one(I do not remember the name right now - am on Ubuntu)...lol It worked.

Wishing you nice day (if it's a day at your place :) )

...I just checked - right click on the applet (closing button) and in options choose "quit" - hope it will help!:-k

---

### Post by aysiu on 2006-07-12
> **weissnich said:**
> If I reboot the panel is gone again,
what can I do???
This is really strange...
In the **Sessions** settings make sure you check the "save session on logout" option.

---

