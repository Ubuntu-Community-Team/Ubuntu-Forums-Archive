---
title: "Can't Get Button Assignment for Side Mouse Buttons"
date: 2009-02-10
forum: General Help
---

### Post by Berrex on 2009-02-10
Hey everyone. I'm running Intrepid and a Logitech MX Revolution. I was pleasantly surprised that everything is working with the mouse straight away except for the side buttons. I figured it wouldn't be a big deal since I've dealt with this before. On my old mouse, an MX500, I would use xbindkeys to assign the side buttons to Alt+Left/Right so that I could use the side buttons to navigate in Opera. Unfortunately, I'm not having much luck this time around with my MX Revolution.

For whatever reason, I simply cannot get a button number assignment for the side buttons. Typically, when I run xev in terminal, it picks up the back & forward buttons as buttons 8 and 9, respectively. However, this time, no matter what changes I try in xorg.conf, both buttons return the following:

```
EnterNotify event, serial 34, synthetic NO, window 0x5200001,
    root 0x13b, subw 0x0, time 2713168, (6,25), root:(722,85),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
```

There is no button number assignment, so I can't therefore configure xbindkeys so that they perform Alt+Left/Right; at least, there's no way that I know of.

Here is what I have in xorg.conf (as suggested from [http://en.opensuse.org/Logitech](http://en.opensuse.org/Logitech)):
```
Section "InputDevice"
 Identifier   "Mouse[1]"
 Driver       "evdev"
 Option       "Phys" "usb-*2.2/input0"   # cat /proc/bus/input/devices
 Option       "CorePointer"
 Option       "ZAxisMapping"        "4 5"
EndSection
```

Finally, in case it helps, this is what I have for my .xbindkeysrc file:
```
"xvkbd  -text "\[Alt]\[Left]""
      m:0x0 + b:8
"xvkbd  -text "\[Alt]\[Right]""
      m:0x0 + b:9
```
Since it relies on having a button number, there's not much I can do until I can get the side buttons recognized as buttons 8 and 9.

Any help on this would be appreciated.

Thanks.

---

### Post by Berrex on 2009-02-11
So nobody has any suggestions at all? I really would like to get such basic functionality out of my mouse...

---

### Post by jonlemur on 2009-02-11
Have you tried the buttons option in xorg.conf?  Something like ```
Option "Buttons" "1 2 3 5 4 6 7 8 9"
```  I don't know what those all do, but I remember needing something like that for my logitech mouse.  man synaptics might help.

---

### Post by Berrex on 2009-02-11
Thanks for the reply. I just gave that a try and, unfortunately, nothing changed. I'm still getting the same output with xev for my side buttons.

---

### Post by Berrex on 2009-02-13
Any more ideas? I still can't seem to get the buttons to work.

---

### Post by Berrex on 2009-02-14
I found the solution. After exhausting all other options, I tried what I should have done to troubleshoot the problem to begin with: I tested xbindkeys in verbose mode:

$ xbindkeys -n -v

When I did this, and clicked the side buttons, it told me that xvkbd wasn't found. So, I did:

$ sudo apt-get install xvkbd

Then I restarted X with a Ctrl-Alt-Backspace, logged back in, ran xev in terminal, and sure enough, it picked up my side buttons as buttons 8 and 9, and the bindings I set in xbindkeys were taking effect. So, now I can use my side buttons to navigate in Opera. Hooray! Again, kudos to jonlemur for the response. I appreciate the help.

---

