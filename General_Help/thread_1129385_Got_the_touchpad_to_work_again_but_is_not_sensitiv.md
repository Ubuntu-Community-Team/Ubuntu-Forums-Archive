---
title: "Got the touchpad to work again but is not sensitive"
date: 2009-04-18
forum: General Help
---

### Post by Lingonet on 2009-04-18
Hello!

I have a little problem. I'm using Ubuntu 8.10.

As you may have read in my other thread my touchpad died when I tried to disable the touchpad tap. However I got it working again and everything is now fine except one thing:
The sinsitivity is now very low and it's very hard to hit the hit the right option on the screen. The cursor is moving very flicky. When I connect a mouse on the other hand, it works fine and smooth!

When I disabled the touchpad tap and when it died, I used Gsynaptics touchpad, but when I chose the option I wanted in the touchpad options the second I closed the window the option was set back to zero, so I couldn't move my cursor. I run this on my Eee PC as said, and the windows are a little too big for the screen and I can't see the button on the bottom end. Do I have to click on that to accept the options, because I'm used to click on the cross. Is this some special program which needs to be clicked on the bottom button?

I really need some help with this!

Thank you in advance!

Henrik

---

### Post by kerry_s on 2009-04-18
i know what you mean, the new xorg is a pain. i'm going to point you to the arch doc for synaptics it's very good and works on other linux as well.
[http://wiki.archlinux.org/index.php/Synaptics](http://wiki.archlinux.org/index.php/Synaptics)

mines a alps, i hate the tapping, i only have tapping on the left bottom corner set to the middle click.

mine:
```
Section "InputDevice"
        Identifier  "Touchpad"
	Driver	    "synaptics"
#        Option	    "TapButton1" "1"
        Option      "LBCornerButton" "2"
	Option      "LeftEdge" "130"
	Option      "RightEdge" "840"
	Option      "TopEdge" "130"
	Option      "BottomEdge" "640"
	Option      "FastTaps" "1"
EndSection
```

---

### Post by Lingonet on 2009-04-19
> **kerry_s said:**
> i know what you mean, the new xorg is a pain. i'm going to point you to the arch doc for synaptics it's very good and works on other linux as well.
[http://wiki.archlinux.org/index.php/Synaptics](http://wiki.archlinux.org/index.php/Synaptics)

mines a alps, i hate the tapping, i only have tapping on the left bottom corner set to the middle click.

mine:
```
Section "InputDevice"
        Identifier  "Touchpad"
	Driver	    "synaptics"
#        Option	    "TapButton1" "1"
        Option      "LBCornerButton" "2"
	Option      "LeftEdge" "130"
	Option      "RightEdge" "840"
	Option      "TopEdge" "130"
	Option      "BottomEdge" "640"
	Option      "FastTaps" "1"
EndSection
```

So how do I solve the "flicky" mouse movement?

---

### Post by kerry_s on 2009-04-19
> **Lingonet said:**
> So how do I solve the "flicky" mouse movement?

flicky? not sure exactly what you mean by that, but try playing with this one:
```
   Option      "AccelFactor"       "0.0020"    # acceleration factor for normal pointer movements
```

---

### Post by Lingonet on 2009-04-19
> **kerry_s said:**
> flicky? not sure exactly what you mean by that, but try playing with this one:
```
   Option      "AccelFactor"       "0.0020"    # acceleration factor for normal pointer movements
```

It's not the acceleration I want to change, it's the sensitivity. The mouse is moving (how do I say this) laggy, hacky and it's hard to move it and hit the right button on the screen.

---

### Post by kerry_s on 2009-04-19
> **Lingonet said:**
> It's not the acceleration I want to change, it's the sensitivity. The mouse is moving (how do I say this) laggy, hacky and it's hard to move it and hit the right button on the screen.

theses are movement:
```
   Option      "MinSpeed"          "0.10"  # speed factor for low pointer movement
   Option      "MaxSpeed"          "0.60"  # maximum speed factor for fast pointer movement

```

did you even read the link i pointed you to?
did you check what kind of touchpad you have? (cat /dev/input/mouse1)
could your touch pad be oily/dirty, i have shs(sweaty hands syndrome) so i have to clean mine often when i use it. 
try googling your symptoms.
there is no right answer you just need to play with the settings.

---

