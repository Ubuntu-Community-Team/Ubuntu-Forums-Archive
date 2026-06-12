---
title: "Something mess up on the desktop"
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by ernestkot on 2008-03-06
Hi, I'm new to ubuntu and I try to run the live CD on my HP dv5000 laptop.
After it booted up, the desktop is kind of mess up as show at the screen shot,
I tired several times but the problem still here.
Is any setting i do /w it,
or it will be ok after i completely install on my computer?

thanks !!

[IMG]http://i35.photobucket.com/albums/d196/ernest_kot/Screenshot.jpg[/IMG]

---

### Post by scrooge_74 on 2008-03-06
You need to adjust the resolution

try Ctrl+Alt+"+" or Ctrl+Alt+"-" ("+"/"-" from the numeric keypad) to change resolutions on the fly

---

### Post by ernestkot on 2008-03-07
thank you

but nothing coming up after Ctrl+Alt+"+" or Ctrl+Alt+"-" 
and i checked the screen resolutions is correct.

still have that problem T_T

---

### Post by ernestkot on 2008-03-07
can anyone help me out please?:(

---

### Post by scrooge_74 on 2008-03-08
then you need to reconfigure your xserver

open a terminal

sudo dpkg-reconfigure xserver-xorg

then when you get to the display section answer the questions as best as possible, if you use expert setting and If you have the sync rates, vertical and horyzontal details you can even be more accurate

---

### Post by chrisccoulson on 2008-03-08
I'm guessing it is to do with window title font size being too large.

Go to System -> Preferences -> Appearance, then go to the Fonts tab and reduce the size of the window title font.

---

