---
title: "remap Mouse Keys"
date: 2011-04-10
forum: Desktop Environments
---

### Post by Felson on 2011-04-10
I have a keyboard that has no Numlock key or number pad. Not even as a function key. Anyone know a way to remap the keys to set mouse keys mode and the keys once it is.

Perfect world, I would be able to use the arrow keys, Right Alt and Right Shift while holding down the windows logo key.

---

### Post by Felson on 2011-04-11
bump

---

### Post by Copper Bezel on 2011-04-11
[This thread]("http://ubuntuforums.org/showthread.php?t=1724914") may be of interest to you. = ) It doesn't look like the script is completely finished, but it's getting there.

---

### Post by Krytarik on 2011-04-15
Please post the output of this command:
```
xmodmap -pke |egrep " 113 | 111 | 114 | 116 | 134 | 108 | 62 "
```
Just to check if they are the same as at my system, should be though.

I already did some fiddling with the Shift key, and it seems like it's not possible to map it like you want. So, please think about an alternative.

Also, if you want to use Super_R (Windows key) as the modifier for the mouse keys, it would eventually remove its feature as Super key and turn it into an additional AltGr key. Of course, we could instead turn AltGr into Super_R. Or we keep both as they are and you use AltGr as they modifier instead.

---

### Post by Felson on 2011-04-15
If I can't use Super_R as a "Shift" key, what about setting it to toggle the mode on and off like Shift-Numlock did? ATM I don't use the Super_R key for anything. That is kinda why I was thinking about it. Is it already used for some functions I didn't know?

```
keycode  62 = Shift_R NoSymbol Shift_R
keycode 108 = Alt_R Meta_R Alt_R Meta_R
keycode 111 = Up NoSymbol Up
keycode 113 = Left NoSymbol Left
keycode 114 = Right NoSymbol Right
keycode 116 = Down NoSymbol Down
keycode 134 = Super_R NoSymbol Super_R

```

---

### Post by Krytarik on 2011-04-15
> **Felson said:**
> If I can't use Super_R as a "Shift" key, what about setting it to toggle the mode on and off like Shift-Numlock did? ATM I don't use the Super_R key for anything. That is kinda why I was thinking about it. Is it already used for some functions I didn't know?

You misunderstood, you *can* use Super_R as modifier to enable the mouse keys (by holding it down), but you probably can't use *Shift_R* as click button. If you choose an alternative, please post the output for those as well, get it's keycode with "xev" before.

The Super keys are by default set for some keyboard shortcuts, for example in "Preferences -> Keyboard Shortcuts" and in Compiz. But you have of course two of them, and if you can give up the right one for the usual Super key feature, it's no problem at all.

---

### Post by Felson on 2011-04-16
Oh cool. Thanks.
Control_L (37) left mouse. 
Alt_L (64) middle mouse and 
Alt_R (108 )

---

### Post by Krytarik on 2011-04-17
> **Felson said:**
> 
Control_L (37) left mouse. 
Alt_L (64) middle mouse and 
Alt_R (108 )
Then please post the mappings of the additional keys as well:
```
xmodmap -pke |egrep " 37 | 64 "
```Are you sure about Control_L as normal (left) mouse click?

Update: After some more fiddling/testing it seems quite sure that we can't set a 3rd keysym to *any* of the keys you want to use. And if we set keysyms of the keypad keys as the primary or secondary keysyms, those can only be controlled by the state of NumLock, which at least leaves us one way to achieve that, but than it's of course either on or off. Also, it seems impossible to map the right-click and middle-click to one of the desired keys, without losing their original functions.

---

### Post by Felson on 2011-04-18
Thanks for trying anyway. I will play with this once I get some time and see what I can do.

---

