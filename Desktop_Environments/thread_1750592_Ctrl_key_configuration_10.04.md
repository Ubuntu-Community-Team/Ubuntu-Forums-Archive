---
title: "Ctrl key configuration 10.04"
date: 2011-05-05
forum: Desktop Environments
---

### Post by AtticHacker on 2011-05-05
Hi,

I've recently installed Ubuntu 10.04 and I've put the ctrl key to alt, and the alt key to the windows key. Now what I've done is:

went to System > Preferences > Keyboard shortcuts and put ctrl + tab to switch windows (ctrl which is now located at alt) 

Now that I've done this it causing a little problem, because ctrl + tab switches tabs instead of windows. Because of this (I think) when I press ctrl + tab it first switches a tab, but then when I press tab again while holding down ctrl it switches windows.

This also happens when I want to access the Launchy app (ctrl + spacebar) I have to press the spacebar twice in order for it to work. This is quite annoying and I hope someone knows how I could fix this. The funny thing is, is that I used to use Ring Switcher in CompizConfig for ctrl + tab and that worked. But then I reinstalled Ubuntu 10.04 and tried it again, but it had the same problem it has now.

So does anyone have any idea how I could fix this? I couldn't find the hot key for ctrl + tab in order to switch tabs. But normally if you set a hot key that's already in use it disables the current used hotkey. 

Any help is appreciated! And I'm really sorry if I posted this in the wrong forum.

---

### Post by Copper Bezel on 2011-05-05
This is definitely the right forum. = ) I don't have an immediate answer, but some directions we can look in.

You can use the command [font="Courier New"]xev[/font] to check what signals your keys are actually sending. It's a little tricky, but you can use it to check exactly what's happening and what signals are being sent when you press Ctrl+Tab the first time and Tab again after that. This will be the place to start.

Passing strange that you'd be getting two different signals sent from the key you're holding down. 

While Alt+Tab is provided by the window manager, Ctrl+Tab is a function within the browser and is rarely configurable. Even in Firefox (known for its flexibility) it requires editing text files.

Edit: Also, what method did you use to rearrange the keys? An xmodmap command, or the Keyboard Preferences manager?

---

### Post by AtticHacker on 2011-05-06
I used System > Preferences > Keyboard to turn alt in to ctrl, and windows key into alt. I just switched it back to normal just now, and if I press ctrl + tab (for Ring Switcher) I still have to press tab twice. Also I tried xev but I wasn't sure what I was looking at. I made screenshots of the results:

Press and release ctrl:
[http://img846.imageshack.us/img846/407/56412797.png](http://img846.imageshack.us/img846/407/56412797.png)

Press and hold ctrl, and press tab twice, release:
[http://img855.imageshack.us/img855/6228/48623382.png](http://img855.imageshack.us/img855/6228/48623382.png)

I'm pretty sure I got ctrl + tab to use Ring Switcher without having to press tab twice. But I have no idea how I did that.

Anyone got any ideas? Thanks in advance.

---

### Post by Copper Bezel on 2011-05-06
By way of explanation, I'm not 100% certain how all of this works, and with xmodmap, I was under the mistaken impression that it was possible to change the keysym without changing the keycode, which is why I asked about xmodmap; however, changing the layout option in Keyboard Preferences changes both, and clearly neither is the actual source of the problem now.

To clarify, with your keymap returned to normal and the Ring set to Ctrl+Tab, when you have to press tab twice, is it only while a browser window is open? (This *shouldn't* have an effect, but it's clear that Ctrl+Tab is somehow skipping the window manager binding and finding its way down to the browser window.

---

### Post by AtticHacker on 2011-05-06
No matter where I am, I have to press tab twice, so it's not just because of the browser.

Edit: But not only do I have to press tab twice, but I have the Application Launchy set to ctrl + space, and I have to press space twice as well. I don't have to press ctrl + C / V / X twice on order to make it work though.

---

### Post by Copper Bezel on 2011-05-06
So strange. If it were global, I could understand it, but some applications are affected and some aren't, and that the window manager is one of the ones that is I find baffling.

Here, try turning off the Compiz keybinding and trying xev again with Control + Tab, just pressing Tab once. (The Compiz plugin causes some confusion in xev as it returns some window management information as well.) This is what I get:

```
KeyPress event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57571987, (-208,278), root:(228,303),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57573767, (-208,278), root:(228,303),
    state 0x4, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "	"
    XmbLookupString gives 1 bytes: (09) "	"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57573914, (-208,278), root:(228,303),
    state 0x4, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "	"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57575400, (-208,278), root:(228,303),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Control pressed, Tab pressed, Tab released, Control released.

---

### Post by AtticHacker on 2011-05-07
> **Copper Bezel said:**
> So strange. If it were global, I could understand it, but some applications are affected and some aren't, and that the window manager is one of the ones that is I find baffling.

Here, try turning off the Compiz keybinding and trying xev again with Control + Tab, just pressing Tab once. (The Compiz plugin causes some confusion in xev as it returns some window management information as well.) This is what I get:

```
KeyPress event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57571987, (-208,278), root:(228,303),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57573767, (-208,278), root:(228,303),
    state 0x4, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "	"
    XmbLookupString gives 1 bytes: (09) "	"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57573914, (-208,278), root:(228,303),
    state 0x4, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "	"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x8c00001,
    root 0xaa, subw 0x0, time 57575400, (-208,278), root:(228,303),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Control pressed, Tab pressed, Tab released, Control released.


Here's what happens for me:

```
FocusOut event, serial 32, synthetic NO, window 0x4400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x4400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  20  0   4294967168 0   32  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 32, synthetic NO, window 0x4400001,
    root 0x110, subw 0x0, time 2001957, (-113,452), root:(550,505),
    state 0x4, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "	"
    XmbLookupString gives 1 bytes: (09) "	"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4400001,
    root 0x110, subw 0x0, time 2002063, (-113,452), root:(550,505),
    state 0x4, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "	"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4400001,
    root 0x110, subw 0x0, time 2002626, (-113,452), root:(550,505),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 35, synthetic NO, window 0x4400001,
    mode NotifyNormal, detail NotifyNonlinear
```

The first obvious thing that I notice is that when I press ctrl I get focus out and focus in. And I also get the KeyRelease. So does that maybe mean when I press ctrl I'm calling 2 functions?



edit: 


When pressing and releasing ctrl key I get this:
```
FocusOut event, serial 41, synthetic NO, window 0x4a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 41, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 41, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
```

Alt key:
```
KeyPress event, serial 41, synthetic NO, window 0x4a00001,
    root 0x110, subw 0x0, time 6742096, (-358,652), root:(548,705),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x4a00001,
    root 0x110, subw 0x0, time 6742198, (-358,652), root:(548,705),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Windows/Super key:
```
KeyPress event, serial 41, synthetic NO, window 0x4a00001,
    root 0x110, subw 0x0, time 6759481, (-281,646), root:(625,699),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x4a00001,
    root 0x110, subw 0x0, time 6759583, (-281,646), root:(625,699),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

This is probably the main problem, the fact that when I press ctrl it uses KeymapNotify instead of KeyPressed. I have no idea how I'm supposed to fix it though.

---

### Post by Krytarik on 2011-05-07
AtticHacker, that is indeed weird, is it the same with the other Control key, Control_R?

Greetings.

---

### Post by AtticHacker on 2011-05-07
Ctrl R works with both ctrl keys.. But I just noticed that when I press and release ctrl some sort of glow effect comes out of my cursor.. I have no idea how that happened and I don't see anything in Compiz. Maybe it has something to do with my ctrl problem? Does anyone know where I could manage those kinds of effects?

Edit: Ok.. So it seems I pressed "Show position of pointer when the Control key is pressed".. And now that I turned it off it's fixed. Man that's stupid haha. Thanks so much for the replies, the xev method really helped.

Thanks again!

---

### Post by Copper Bezel on 2011-05-07
Huh, that would do it. Glad you got this figured out. = )

---

