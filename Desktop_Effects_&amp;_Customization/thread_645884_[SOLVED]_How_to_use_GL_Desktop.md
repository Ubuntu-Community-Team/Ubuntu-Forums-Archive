---
title: "[SOLVED] How to use GL Desktop"
date: 2007-12-20
forum: Desktop Effects &amp; Customization
---

### Post by IanB2 on 2007-12-20
I've seen the really impressive effects that can be achieved in various videos and have managed to achieve some using GL Desktop ....... very nice. 

(I've also installed the full compizconfig but this is totally baffling to the new user so I'm back to GL Desktop)

However, I've been googling to try and find a simple 'how to' use the GL Desktop so I can get the maximum benefit. It is not always very clear what an effect actually does and I've only managed to get some working.

Any suggestions would be appreciated :)

---

### Post by Espreon on 2007-12-20
Actually the goal of "GL Desktop" is that not all the Compiz effects will be available. Its meant for simplicity. I would not describe CCSM as "baffling", you just need to play around with it a little to figure out what things do.

---

### Post by IanB2 on 2007-12-25
Some 'help files' or guide for GL desktop or compiz fusion would be nice.
There are loads of videos on the effects that can be created but little info on HOW this was done.

I've played around a little but don't have the time to try all combinations.
The spinning cube in the centre of the screen was the effect I was trying to achieve but with no success so far. I'm a little confused by the number of 'desktops' or 'workspaces' that are required and how to set these up for the cube effect.

---

### Post by Tanjer1588 on 2007-12-25
hey i found this howto: the other day on how to make your desktop your own, so if the GL dont work out try some of these aproches

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by shareMenaPeace on 2007-12-25
GL Desktop realyl confused me first, i would suggest uninstall it and get 

compizconfig-settings-manager from the repos (synaptic install).

Also i use 

ubuntu-tweak.com for some mor enice compiz stuff and other nice things...

---

### Post by Forlong on 2007-12-25
Just don't use "GL Desktop" witch Compiz Fusion. It's not designed to work with it:
```
sudo apt-get remove --purge gnome-compiz-manager
```
There's no way around ccsm
```
sudo apt-get install compizconfig-settings-manager
``` for now.

Simple-ccsm is in development though: [http://dev.compiz-fusion.org/~marex/category/ccsm/](http://dev.compiz-fusion.org/~marex/category/ccsm/)

---

### Post by Mr Fredrick on 2007-12-25
I'm new to Ubuntu too and have just spent the last few hours googling GL Desktop because I found it confusing and wondered how it fits in with the whole Advanced Desktop Effects thingy. I wasn't sure if I should run it or not !

Are you certain it can be removed without harm?

AND IS:

sudo apt-get remove --purge gnome-compiz-manager

the correct way to do it.

Regards,

Mr Fredrick

---

### Post by Forlong on 2007-12-26
> **Mr Fredrick said:**
> Are you certain it can be removed without harm?

AND IS:

sudo apt-get remove --purge gnome-compiz-manager

the correct way to do it.
Yes, otherwise I wouldn't have posted it. :)

---

