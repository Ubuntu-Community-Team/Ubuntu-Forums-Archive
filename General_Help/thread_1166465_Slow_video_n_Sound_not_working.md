---
title: "Slow video n Sound not working"
date: 2009-05-21
forum: General Help
---

### Post by Abecsta on 2009-05-21
I installed 9.04 and everything was working fine had sound could watch videos and listen to music. But then it just stoped i was listening to some music and then my sound just started making weird noises and now it always does that but sometimes plays startup sound. with video i can watch it in vlc but no sound. and in the default player its like watching it frame by frame.
ive tryed a few things like installing the pulse audio which i follow some guide for.
 
i have a toshiba satellite which has an 
ati radeon xpress 200m graphix card
 
note i dont really know anything about ubuntu this has been my first try of it
apart from the sound and video problems i think its pretty mean
 
(i can reinstall again if that helps but it never fixes it & if you need more info on the laptop i can give u that when i get home)

---

### Post by Abecsta on 2009-05-22
so i reinstalled and then played the ubuntu video in examples and that worked fine so i downloaded vlc and put a movie on it played fine for a while then the sound stoped and started making the weird noises and now sound isnt working

---

### Post by QIII on 2009-05-22
How old is your Toshiba?

There are a lot of older ATI Radeon cards whose driver support has been discontinued.

---

### Post by Abecsta on 2009-05-22
its rather old its a m50 
and if i go aplay -l


card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
that comes up
the main issue for me is sound i got vlc playing videos like normal just no sound

---

### Post by Abecsta on 2009-05-25
so any1 got any advice on how to get sound working as it works sometimes but yea

---

### Post by Steelmourne on 2009-05-25
Try going into system preferences and sound and testing sound there. It should be set to autodetect. Post the output of this lspci -vv | grep Audio from terminal.    

Otherwise try this:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

