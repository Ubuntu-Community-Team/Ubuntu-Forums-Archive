---
title: "Joystick thinks it's a mouse.."
date: 2010-05-05
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2010-05-05
I'm aware that G&L isn't the perfect place for this but given the surge of people getting the Humble Indy Bundle these last couple days I figured someone else might have had a similar issue and solved it.  :p

I first noticed the issue when I was playing Gish for the first time in years.
In level 2-3 or so you need precise control as well as the ability to hit more than two keys at the same time, a luxury my wireless keyboard does not provide.
So I plugged in my trusty Saitek and got to configuring the joystick controls... or so I thought..
The second I hit any axis X crashed and I was back at my login screen.  >.>
Tested this with KDE (my default) and Gnome and have had the same trouble with each, leaving me to believe that X is the source of my troubles.
The crash only occurs when a fullscreen program has focus, if there is no such program the cursor will just jump around the desktop when I hit the directional pads.

I did find a few bug reports about a similar issue but they were years old and dealt with HAL which has since become defunct.

So if any of you out there have the slightest clue how I can resolve my issue I'd greatly appreciate it.  ^_^

--Aaron

---

### Post by hikaricore on 2010-05-07
Bump for great justice!

---

### Post by sepius on 2010-05-21
I have the same issue with my Logitech Wingman.  Still looking for a result.  I have had this in the past (long long time ago) and cannot remember how to fix, but it has made flying in Flightgear a tad tricky.

---

### Post by sepius on 2010-05-22
Found a little post [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1477206") where janagn removed the package xserver-xorg-input-joystick.  I did the same and restarted the whole system and now my wingman works fine with Flightgear, just needs a recalibrate now..

---

### Post by hikaricore on 2010-05-22
Sadly that package is not installed on my system.  :p
Thanks for tryin though.

---

