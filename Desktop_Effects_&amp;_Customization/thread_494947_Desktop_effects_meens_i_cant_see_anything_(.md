---
title: "Desktop effects meens i cant see anything :("
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by kablooee on 2007-07-07
I am a linux novice and was fiddling  with the fancy sounding preferences when i pressed desktop effects and everything dissapeared. the whole screen went white except my mouse and I can still click things as after about five minutes I managed to log out. Now when I log back in on any sessions it's still blank, except terminal.
Is there a terminal shortcut to turn off desktop effects or something? I'm forced to run this off vista, the biggest waste of money ever sold. ever.

---

### Post by Happy_Man on 2007-07-07
Umm.... there's not a way to disable Compiz from the command line.....Sorry. I remember I fixed my problem by using the command ```
sudo apt-get remove --purge compiz-core desktop-effects
``` I then reinstalled it by using the command ```
sudo apt-get install compiz-core desktop-effects
``` See if that works.

---

### Post by mad4dweb on 2007-09-01
The magik comand that made me recover from the white screen 
> sudo apt-get remove --purge compiz-core desktop-effects
REBOOT


I was playing with the screenlets and compiz i dont remember what i activated but my screen went white and i only could see ALT+TAB keys option 

I tested all posible solutions mentioned on the forums but none worked for me. 
     - Like changin the driver in xorg.conf to vesa
     - Doing compiz --replace
     - and some other solutions mentioned in this forum and google

I have a Unichrome card so the Nvidia solution was not what i was looking for.

THANKS Happy_Man

---

### Post by Inxsible on 2007-09-01
Since your terminal works, try ```
metacity --replace
```

---

### Post by skuli.arnlaugsson on 2007-09-03
> **Happy_Man said:**
> Umm.... there's not a way to disable Compiz from the command line.....Sorry. I remember I fixed my problem by using the command ```
sudo apt-get remove --purge compiz-core desktop-effects
``` I then reinstalled it by using the command ```
sudo apt-get install compiz-core desktop-effects
``` See if that works.

It didn't do it for me, any more ideas?

---

### Post by coqui1212 on 2007-09-05
It worked for me, thanks!

---

### Post by beefcurry on 2007-09-06
Have this problem using Gutsy Tribe 5. However stuck with  Couldn't find package desktop-effects. Looks like im up for a full reinstall.

---

