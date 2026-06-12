---
title: "Nasty display: extra pixels everywhere"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Keith_Beef on 2006-09-03
Not sure how to describe this in a short way for the thread title...

I had a problem with icons and other widgets being badly displayed since I upgraded from Breezy to Dapper. There were extra pixels (mostly a shade of pale blue) here and there. But when I moved the mouse pointer over a widget, it would be redrawn correctly. I could live with it, andexpected it would be corrected in an update.

But last night, after being away from the keyboard for a month, I had 154 upgrades waiting to be installed. After this update, the problem has worsened dramaticaly as you can see from the screenshot of the Ubuntu welcome page.

[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/problem_1_small_thumb.png[/IMG]](http://i71.photobucket.com/albums/i121/Keith_Beef/Ubuntu/problem_1.png)

Any idea what I can do about this?


Thanks in advance,
Beef.

---

### Post by foolsh on 2006-09-03
i dont know your specs but it sounds like and old video card problem, I use old pci cards as secondary display adapters on all my boxen 
and have seen stange things on them
if in fact this is the case 
```
sudo gedit /etc/X11/xorg.conf
```
and add
```
Option "ShadowFB" "True"
```
to your device section 
sorta like this

```
Section "Device"
        Identifier      "matrox"
        Driver          "mga"
        BusID           "PCI:3:1:0"
        Option          "ShadowFB"      "True"
EndSection
```

and save then restart X with control+alt+backspace
and see if the "extra pixels" are still there
im not certian but using this option might include a performace hit but if its an old card then what the hell did you lose anyway

---

### Post by Keith_Beef on 2006-09-04
Would you believe it? Since I switched off overnight and rebooted, the problem as I described has cleared up!

I still see some extra pixels around widgets, but nowhere near as bad as what I described in my post.

I'm at a complete loss as to the cause, or the cure. :?


K.

---

