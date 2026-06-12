---
title: "beryl + incorrect config = killed desktop!! :("
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by davebell on 2007-08-17
ok heres wats happened:
ive had ubuntu installed happily with beryl, yet was having problems playing movies, i looked for a little while to find a fix to the problem to no avail, so decided to try my hand at fixing my own problems: BAD IDEA!! i tried changing some of the advanced settings and changed the rendering platform(i think) to nvidia, this completely stuffed ubuntu, i can start up and login, but after login nothing works, it shows window borders, but nothing inside, none of the effects work...NOTHING! its literally killed my computer.
My question to you, kind friend is this: is there anything which i can do (ie terminal commands) to either disable/uninstall beryl or to change the setting back to automatic.

plz your help would b very much appriciated!!!
thank you in advanced.
david

---

### Post by hyperair on 2007-08-17
There is: ```
rm ~/.beryl-managerrc
```
After that, just log in. Everything should be fine.

---

### Post by drwindow on 2007-08-17
And once again, the shell saves the day.....

---

### Post by ZipoTe on 2007-08-17
> **davebell said:**
> ...so decided to try my hand at fixing my own problems: BAD IDEA!! i tried changing some of the advanced settings and changed the rendering platform(i think) to nvidia, this completely stuffed ubuntu...

Not a bad idea, just a bad result. This is the right way of learning, you must try to do new things and if they go wrong, look for help and learn :)

---

### Post by rbolio on 2008-04-10
> **hyperair said:**
> There is: ```
rm ~/.beryl-managerrc
```
After that, just log in. Everything should be fine.


I had a similar problem...will this fix the problem permanently or do i have to run the comand  everytime?

---

### Post by hyperair on 2008-04-10
Permanently if you don't screw it up again.

---

### Post by rbolio on 2008-04-28
awsome!..... thanks!

---

### Post by vikasvishnu on 2008-04-30
> **ZipoTe said:**
> Not a bad idea, just a bad result. This is the right way of learning, you must try to do new things and if they go wrong, look for help and learn :)

Right said, Friend :) Try and learn! its not going to blow your computer anyways! 

Vikas

---

