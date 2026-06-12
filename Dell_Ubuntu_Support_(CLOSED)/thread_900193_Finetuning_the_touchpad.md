---
title: "Finetuning the touchpad"
date: 2008-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 4Play on 2008-08-25
Hello, I have a XPS M1530 with 64-bit Hardy. I am trying to improve my touchpad's usability, bucause even after installing gsynaptics and using the boot parameter so the pointer wont go crazy, I find the touchpad very, very bad. This is mostly due to two reasons: its too sensitive to clicking, simply moving my finger across the touchpal will, more often than not, click everything in it's path...very annoying. also the horizontal scroll is a joke, i have to press my finger against the corner of the touchpad area and start scrolling from the very top (or bottom) otherwise it wont work. Also,, the touchpad driver seems to randomly decide not to load, requiring some reboots until it feels like coming back...but this isnt so irritating as the other two things.

So I was wondering if someone has tweaked they'r touchpad via xorg.conf or some utility other than gsynaptics, which simply isnt cutting it. I wanted to increase the horizontal scroll zone, and decrease the touchpad's sensitivity to clicking.

This is one of the things that have been irritating me profusely, but all my efforts always lead to the same "use gsynaptics" solution.

Many thanks for **any** help here :D

---

### Post by trwww on 2008-08-25
I use qsynaptics. I edit my ~/.qsynaptics file by hand, and then run [FONT="Courier New"]qsynaptics -r[/FONT] to get qsynaptics to send the new touchpad settings to load in to the system.

Here is the custom settings I'm using:

```
ClickTime is 3
FingerHigh is 45
FingerLow is 32
MaxDoubleTapTime is 3
```

trwww

---

### Post by 4Play on 2008-08-25
thanks! that helps a lot, for some reason setting the options via the gui was not effective, but manually editing the file worked, thanks...now all i have to resolve is why the driver doesnt initialize half of the times i start linux...

thanks :)

---

