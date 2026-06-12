---
title: "Switching Keyboard Layouts gets rid of the &quot;Left Key&quot; regardless of xmodmap"
date: 2010-07-24
forum: Desktop Environments
---

### Post by Cyclops_ on 2010-07-24
I have two layouts defined, one for US Qwerty and one for Programmer Dvorak.

In US Qwerty, I have the use of the Left arrow key.  When I switch to Dvorak, I don't have it anymore (except when I press Control-Alt-Left to make my Compiz cube rotate).

When I switch back to US Qwerty, I have it again.

In Qwerty, here is the output of xev when I press the Left arrow key:

```

KeyRelease event, serial 34, synthetic NO, window 0x4000001,
    root 0x52, subw 0x0, time 91221599, (335,-238), root:(4182,658),
    state 0x90, keycode 113 (keysym 0xff51, Left), same_screen YES,
    XKeysymToKeycode returns keycode: 100
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

In Dvorak:

```

KeyRelease event, serial 34, synthetic NO, window 0x4000001,
    root 0x52, subw 0x0, time 91223271, (335,-238), root:(4182,658),
    state 0x2010, keycode 113 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Here are the contents of my ~/.Xmodmap (which I assume both layouts are using???):

```

keycode 50 = Shift_L
keycode 104 = KP_Enter
keycode 105 = Control_R
keycode 106 = KP_Divide
keycode 107 = Print
!keycode 108 = Alt_R
keycode 108 = ISO_Level3_Shift
keycode 110 = Home
keycode 111 = Up
keycode 112 = Prior
keycode 113 = Left
keycode 114 = Right
keycode 115 = End
keycode 116 = Down
keycode 117 = Next
keycode 118 = Insert
keycode 119 = Delete
keycode 121 = XF86AudioMute
keycode 122 = XF86AudioLowerVolume
keycode 123 = XF86AudioRaiseVolume
keycode 127 = Pause
keycode 133 = Super_L
!keycode 134 = Super_L
keycode 135 = Menu
keycode 148 = XF86Calculator
keycode 150 = XF86PowerOff
keycode 156 = XF86Launch1
keycode 157 = XF86Launch2
keycode 163 = XF86Mail
keycode 169 = XF86Eject
keycode 171 = XF86AudioNext
keycode 172 = XF86AudioPlay XF86AudioPause
keycode 173 = XF86AudioPrev
keycode 180 = XF86HomePage
keycode 210 = XF86Launch3
keycode 225 = XF86Search
keycode 244 = XF86Launch4
add Mod4 = Super_L
add Mod1 = Alt_R
add control = Control_R

```

As you can see, there is a line:

keycode 113 = Left

....

Does anyone have a clue either to what's going on, or to how I can troubleshoot / fix the issue?

Many thanks in advanced!

---

