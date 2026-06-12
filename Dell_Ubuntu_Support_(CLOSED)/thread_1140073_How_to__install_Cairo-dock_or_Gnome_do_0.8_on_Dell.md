---
title: "How to  install Cairo-dock or Gnome do 0.8 on Dellbuntu"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-04-27
Hi,
i want to install some dock to replace one panel-i am looking for some dock that can be installed one dell´s Ubuntu 8.04 and which is not using compiz/only metacity (whitout compositing manager). Is that possible? I tried AWN-works fine, but "metacity compositing manager" slows a little bit dell mini 9. Cairo Dock and Gnome Do´s Docky seem fine, but i don´t know how to install them...because i am newbie...
Thanks

I posted this thread also on mydellmini.com

---

### Post by fabounet on 2009-04-28
[http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en]("http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en")

---

### Post by vickoxy on 2009-04-28
Thanks, but i do not want to  activate compositing manager...so is it possible to do it whitout it?

---

### Post by vickoxy on 2009-04-28
Ok  i installed xcompmgr to run cairo-dock 2.0 but there is black border around dock when it pops out. What should i do to make it work fine....?

---

### Post by fabounet on 2009-04-29
is xcompgr running ?
alternatively, you can activate the fake transparency inside Cairo-Dock.

---

### Post by vickoxy on 2009-04-29
i  fixed it-i have to activate xcompgr by start up-restart and everything works just fine. Cairo-dock is the most stable and fastest for LPIA 8.04, but i still have these glitches when i switch tabs and apps, but it is nothing serius. Does anyone knows is there way to fix that, or i have to live with it? It has nothing to do with cairo-dock, but with xcompgr..
Thanks

---

### Post by 666porcondissaum on 2009-05-21
Gnome Do 0.8.1 + Docky in Hardy Heron 8.04:

Gnome Do 0.8.1 + Docky on Hardy Heron 8.04:

Enable the repository shown in the site below:

[http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)

Update and Reboot. Doesn't matter if Gnome 0.6* is installed or not. (Maybe if isn't you'll need to do so... I really don't know). Thks!

Sorry don't ask me for compositing questions but the Docky is already available dor Hardy users.

---

### Post by ozorba on 2009-05-22
> **vickoxy said:**
> i  fixed it-i have to activate xcompgr by start up-restart and everything works just fine. Cairo-dock is the most stable and fastest for LPIA 8.04, but i still have these glitches when i switch tabs and apps, but it is nothing serius. Does anyone knows is there way to fix that, or i have to live with it? It has nothing to do with cairo-dock, but with xcompgr..
Thanks

Yes! cairo-dock 2.0 is very nice. I am impressed.

I have added it to the startup application list and whenever I login I get the cairo-dock configuration menu. Is there a way to stop this?

BTW. I am using Ubuntu 9.04

TIA

---

### Post by fabounet on 2009-05-22
how do you launch it ?
do you force one of the backend ? (option -c or -o)
what if youlaunch it from the menu ?
did you try to launch it with a delay on startup ?

---

### Post by ozorba on 2009-05-22
> **fabounet said:**
> how do you launch it ?
do you force one of the backend ? (option -c or -o)
what if youlaunch it from the menu ?
did you try to launch it with a delay on startup ?

If I launch it from menu it is fine. BTW I have used -c option. -o option does not work well.

---

### Post by fabounet on 2009-05-22
so you probably should add a delay on startup (to let Compiz load I guess)
```
#!/bin/bash
sleep 10
cairo-dock -c
exit 0
```

---

