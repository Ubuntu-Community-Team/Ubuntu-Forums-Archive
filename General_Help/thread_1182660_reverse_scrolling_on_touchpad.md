---
title: "reverse scrolling on touchpad"
date: 2009-06-09
forum: General Help
---

### Post by zhocchao on 2009-06-09
I enabled two finger scrolling on synaptics touchpad. Is it possible to reverse the direction of the scrolling (finger goes up-picture goes up. As moving a paper)

---

### Post by zhocchao on 2009-06-16
?

---

### Post by ezramorris on 2009-06-16
> **zhocchao said:**
> I enabled two finger scrolling on synaptics touchpad. Is it possible to reverse the direction of the scrolling (finger goes up-picture goes up. As moving a paper)

Hi,
Press Alt+F2, and type
```
gedit .Xmodmap
```
When it loads up, paste in the configuration you want:
[LIST]
[*]Normal:
```
pointer = 1 2 3 4 5 6 7 8 9 10 11 12
```
[*]Vertical reversed:
```
pointer = 1 2 3 5 4 6 7 8 9 10 11 12
```
[*]Horizontal reversed:
```
pointer = 1 2 3 4 5 7 6 8 9 10 11 12
```
[*]Both reversed:
```
pointer = 1 2 3 5 4 7 6 8 9 10 11 12
```
[/LIST]
Note how 4 and 5, and 6 and 7 change depending on what you want.

Now log out and log in again. When you log in you'll probably be asked if you want to load a config file. Just click on ".Xmodmap", then "Load", then "OK".

Then you should be set to go!

Hope this helps.

---

### Post by zhocchao on 2009-06-17
Somehow xmodmap has no effect. According to xev buttons 4 and 5 are the right one. Xbindkeys doesn't work with my touchpad anymore. Did it in Hardy. Maybe I should try it with xorg.conf?

---

### Post by ezramorris on 2009-06-17
> **zhocchao said:**
> Somehow xmodmap has no effect. According to xev buttons 4 and 5 are the right one. Xbindkeys doesn't work with my touchpad anymore. Did it in Hardy. Maybe I should try it with xorg.conf?

Hmm, odd.

Are you sure you haven't changed 2 things and they are canceling each other out?

Just another thought - maybe using gsynaptics and SHMConfig disables Xmodmap or something.

Maybe you could try
```
Option		"ZAxisMapping"		"5 4"
```
under the InputDevice Section for Synaptics Touchpad in xorg.conf, and log out and in again.

---

### Post by zhocchao on 2009-06-17
Still no luck. My xorg.conf lines:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option		"ZAxisMapping"		"5 4"
EndSection

Tried enable/disable SHMConfig. Still no changes.

Maybe I should play around with /etc/hal/fdi/policy?

ps:how to code tags

---

### Post by ezramorris on 2009-06-17
> **zhocchao said:**
> Still no luck. My 
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option		"ZAxisMapping"		"5 4"
EndSection

```

and "4 5" doesn't work either?

---

### Post by zhocchao on 2009-06-17
no

---

