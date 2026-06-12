---
title: "keys stuck in games"
date: 2010-08-09
forum: Gaming &amp; Leisure
---

### Post by nknwn666 on 2010-08-09
whenever i want to play Frogatto&Friends, after the game loads and i have to move the character, the character just gets stuck moveing left, tried Open Sonic too and the same problem just that here its stuck up and left, same with ExtremeTuxRacer. tried changeing keyboard layout and stoped auto repeat on keys and it didnt fix it. other games work fine

---

### Post by nknwn666 on 2010-08-14
bump...

---

### Post by frenchn00b on 2010-08-15
> **nknwn666 said:**
> whenever i want to play Frogatto&Friends, after the game loads and i have to move the character, the character just gets stuck moveing left, tried Open Sonic too and the same problem just that here its stuck up and left, same with ExtremeTuxRacer. tried changeing keyboard layout and stoped auto repeat on keys and it didnt fix it. other games work fine

I sometimes use debian it is more stable than ubuntu

if you think that it is due to the deb, you can try those ones:
[http://packages.debian.org/search?keywords=frogatto](http://packages.debian.org/search?keywords=frogatto)

---

### Post by nknwn666 on 2010-08-15
same thing..[img]http://serve.mysmiley.net/sad/sad0139.gif[/img]

---

### Post by frenchn00b on 2010-08-15
> **nknwn666 said:**
> same thing..[img]http://serve.mysmiley.net/sad/sad0139.gif[/img]

i am sure if i try with debian testing it will work

```
whenever i want to play Frogatto&Friends, after the game loads and i have to move the character, the character just gets stuck moveing left, tried Open Sonic too and the same problem just that here its stuck up and left, same with ExtremeTuxRacer. tried changeing keyboard layout and stoped auto repeat on keys and it didnt fix it. other games work fine
```


Please post your problem here
[http://www.frogatto.com/forum/](http://www.frogatto.com/forum/)

I would like to help you 

is for instance your keyboard/joystikc wokring when playing on the regular tux cart or other linux games;

maybe it is coming from sdl

---

### Post by nknwn666 on 2010-08-15
> **frenchn00b said:**
> 
is for instance your keyboard/joystikc wokring when playing on the regular tux cart or other linux games;

maybe it is coming from sdl
hedgewars, astromenace, super tux, tasty static and supertuxkart work perfectly
didnt post there beacouse the problem happends with more games then just frogatto
LE: with keyboard unpluged it still gets stuck moving left

---

### Post by nknwn666 on 2010-09-06
ubuntu was detecting my usb mouse as a mouse and joystick. fixed by running:
```
sudo rm /dev/input/js0
```
in terminal everytime at startup

---

### Post by Yfrwlf on 2012-05-05
> **nknwn666 said:**
> ubuntu was detecting my usb mouse as a mouse and joystick. fixed by running:
```
sudo rm /dev/input/js0
```
in terminal everytime at startup

Thanks, solved all my problems!  OpenTyrian was acting like "up" was stuck down, and Oblivion was acting like forward and left were stuck down, when it was an uncalibrated joystick and wrongly detected mouse or something to blame the entire time.  I will check if my mouse is to blame the next time I get the chance.

What is your brand and model of mouse?  Mine is a X7 XL-760H.

---

