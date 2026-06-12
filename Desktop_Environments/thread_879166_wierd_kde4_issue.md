---
title: "wierd kde4 issue"
date: 2008-08-03
forum: Desktop Environments
---

### Post by stlouis1 on 2008-08-03
im having a somewhat wierd kde4 issue here. basically, i had some issues before when i tried updating. so now im on a clean install

but the minute i put kde 4 on my system. essentially, what happens is i can't type at the login screen, or use the mouse. so i can log in.

strangely enough, i can use ctrl+alt+f6 to switch to a terminal. and my keyboard works there

any thoughts? im determined to get it working. i've seen screenshots, but haven't been able to use it yet

---

### Post by AdamWood on 2008-08-04
It sounds like a Xorg problem not detecting your keyboard/mouse. Though I'm at a loss as to why that would happen when you install KDE4.

If you can get to a terminal you could try the following commands

```
sudo /etc/init.d/kdm stop
startx

```
Any output to the terminal might be useful and if it's only a login problem you might be able to see if KDE4 is actually working.

---

### Post by stlouis1 on 2008-08-05
well, i tried that, after trying to go back to kde3 and had the same issue.

but basically, when i run startx, i get a message that its not a valid command. i tried it on my desktop, and it worked fine.

somethings screwy here, its aggravating me

---

