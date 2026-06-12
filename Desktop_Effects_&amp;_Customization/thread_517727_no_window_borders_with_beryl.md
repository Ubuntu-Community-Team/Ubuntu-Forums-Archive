---
title: "no window borders with beryl"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by maxi123 on 2007-08-04
i have an ATI mobility radeon x600 graphics card and i installed beryl and emerald.... but i get no window borders... everything else works

any help fixing this is greatly appreciated

---

### Post by damnitpud on 2007-08-04
to get some borders back open a terminal and type in metacity --replace hit enter and now you have your borders back.

Also try following this guide to get beryl or compiz working.
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by maxi123 on 2007-08-04
beryl works... i just dont have any window borders =/ i know i can go back to metacity and have them but then its not beryl... 

ive tried emerald --replace but that doesn't do anything

thanks again for any help

---

### Post by atomkarinca on 2007-08-05
> **maxi123 said:**
> beryl works... i just dont have any window borders =/ i know i can go back to metacity and have them but then its not beryl... 

ive tried emerald --replace but that doesn't do anything

thanks again for any help

i don't think without emerald, beryl is somewhat incomplete. i use metacity as windows decorator and much more satisfied that using emerald. there are very good gtk themes [here]("http://www.gnome-look.org"). and if you're using kde, then you can check out some themes [here]("http://www.kde-look.org").

---

### Post by maxi123 on 2007-08-05
ya but then i'd have to install compiz and it was hard enough to get beryl working with my graphics card :P so i'd just like to see if theres a way to get my window borders going with emerald.... thanks

---

### Post by maxi123 on 2007-08-05
bump :)

---

### Post by GadgetsGuy on 2007-08-07
Bump for an answer ... I have the same problem

---

### Post by Zyppora on 2007-08-07
I've had this problem as well (ATi Radeon A9250). What I've come to know through trial and error (and LOTS of 'ps -A'ing) is that you need three processes to run:

- beryl-manager
- emerald
- beryl

(usually in this order, not sure if that's mandatory)

Use ps -A to see which processes are running and find if any of those three are missing. I'm thinking your emerald process is not running if your borders (and titlebar?) are missing.

Just another ubuntu newbie posting his experiences :)

---

### Post by GadgetsGuy on 2007-08-07
After spending all of last night --and most of today-- trying to get all the ghosts out of my machine ... this seems to work to bring back borders with NVidia cards running emerald-manager

```
$ sudo gedit /etc/X11/xorg.conf
```

In the Devices section add:

```
Option         "AddARGBGLXVisuals" "True"
``` 

and then reboot

---

### Post by rgiskard01 on 2007-08-18
I was having same problem...that worked for me as well!

---

