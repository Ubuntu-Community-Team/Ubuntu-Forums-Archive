---
title: "Mouse axis flip with Intrepid"
date: 2008-11-04
forum: Desktop Environments
---

### Post by grahamrjuk on 2008-11-04
With Hardy I was able to invert one of my mouse axes and then flip X and Y effectively roatating the mouse by 90 degrees.

With the new input set-up in X with Intrepid I can't yet find a way to do that.

I see info on a number of ways to alter mouse behaviour (HAL, XRandR etc) but the docs I find are not clear enough to suggest how to do the axis flip.

Any help is much appreciated :-)

---

### Post by judas3000gold on 2008-12-07
me too, i'm on a asus eeepc and i can rotate the screen so i can hold it like book, but the touchpad is not rotated, which makes it really difficult to operate

---

### Post by coCoKNIght on 2009-07-09
Subscribing. I want to be able to invert up and down in order to be able to play good old cyberia. Have tried a bit with xorg and hal but to no avail...

Afaik the mouse directions are treated like buttons. If so, remapping the buttons would do what we want. I think the [Logitech Marble Mouse USB]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB") article in the Community Docs is quiet interesting, but although I was able to rearrange the buttons, I wasn't able to change the axes yet...

---

### Post by diegorodriguezv on 2009-10-31
I'm in the same situation.

In Hardy I can invert my Genius Traveler 350 trackball with the following section in /etc/X11/xorg.conf:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        # Invert Axes
        Option          "InvX"          "1"
        Option          "InvY"          "1"
        # Invert wheel-up / wheel-down
        Option          "ZAxisMapping"  "5 4"
        # Invert middle and right mouse buttons
        # Invert back and forward buttons also
        Option          "ButtonMapping" "1 3 2 9 8"
EndSection

```

But it doesn't work in Jaunty or Karmic. I'm sure that the xorg.conf file is being read because it says so in the /var/log/Xorg.0.log file.

My guess would be that the new ultra-fast-auto-configuration-driver-architecture loads another "mouse" driver or it loads it on the fly without passing the arguments or something like that.

Any guess? Some ideas? Pointers? Help?

Thank you.

---

### Post by diegorodriguezv on 2009-11-01
Ok. Just to let you know I now have my axes inverted in Karmic :D. Just had to use the following commands:

```

xinput set-button-map "KYE  Traveler 350" 1 3 2 5 4 6 7 9 8
xinput set-int-prop  "KYE  Traveler 350" "Evdev Axis Inversion"  8 1 1

```

They do the same as the xorg.config posted above.

---

