---
title: "Kdm boot problem, Gutsy downgrade"
date: 2007-08-14
forum: Desktop Environments
---

### Post by ax-ax on 2007-08-14
I run 7.04

1. I tried a kernel update, and added a Gutsy rep. I forgot to remove it. Then I accidentaly runned apt-get upgrade instead of update and 700 programs updated  ](*,)
I havee removed that rep now, but the programs are still updated, is there any way to downngrade them to fiesty again?

2. I installed KDE-desktop and chose KDM as login manager. But when it starts, there is:
     - A cursor
     - My background
     - A white terminal box
If I run 'firefox', it opens firefox whitout window borders. It's probably fail-saafe-mode or something, but i can't get it to work normaly, tried tty and stopping kdm and startx. :confused:

3. I put in a picture when I boot, so it's shown when I chose kernel, but i think I don't want it, it doeesn't work. I can't find the tutorial of how to remove it, so i aask here instead.

Sorry if my keyboaard doesn't obay.

---

### Post by prince_niceguy on 2007-08-23
I am not sure if you will be to downgrade. Try updating to gusty now fully :-)... I had gusty upgrade for sometime and for downgrade I had to reinstall.

try doing

sudo apt-get dist-upgrade

this will upgrade to gusty. Not sure of any other way.

---

