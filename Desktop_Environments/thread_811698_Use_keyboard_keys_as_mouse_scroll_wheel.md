---
title: "Use keyboard keys as mouse scroll wheel"
date: 2008-05-29
forum: Desktop Environments
---

### Post by xenocard on 2008-05-29
I have a multimedia keyboard with two Back and Forward buttons that I never use. I'd like to remap them into mouse wheel events: Back would be used to scroll up, Forward to scroll down.

Xkb provides two keysyms that seem to fit my needs: XF86ScrollUp and XF86ScrollDown. I managed to remap my keys to those keysyms, as shown by xev:
```

KeyPress event, serial 30, synthetic NO, window 0x3e00001,
    root 0x3f, subw 0x0, time 113913610, (60,145), root:(65,167),
    state 0x10, keycode 234 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3e00001,
    root 0x3f, subw 0x0, time 113913610, (60,145), root:(65,167),
    state 0x10, keycode 234 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x3e00001,
    root 0x3f, subw 0x0, time 113914170, (60,145), root:(65,167),
    state 0x10, keycode 233 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3e00001,
    root 0x3f, subw 0x0, time 113914170, (60,145), root:(65,167),
    state 0x10, keycode 233 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

However, my windows wouldn't scroll. They do scroll only if I enable the MouseKeys mode (controlling the mouse with the keypad by pressing Shift+NumLock). Obviously it's not what I want.

So, I was wondering if anyone would have any idea how I could make those keysyms work even when the MouseKeys mode is disabled? Or is there any other means to map mouse events onto keyboard keys?

Thanks

---

### Post by ario on 2009-05-06
Hi.
I have the same problem.
I already reading this tread. You may look at this and find it useful:
[https://help.ubuntu.com/community/TrustMultimediaScrollKeyboardKB-2200](https://help.ubuntu.com/community/TrustMultimediaScrollKeyboardKB-2200)

---

### Post by lautarop on 2009-05-20
bump?

---

### Post by rorzik on 2009-09-22
I had a similar desire today to map the XF86Back and XF86Forward buttons on my laptop to scroll up and scroll down, so let me post the solution.  First, identify the keycodes (166 and 167 in my case) that you want to map using the command xev.

Then edit ~/.Xmodmap like this:

```
keycode 166 = XF86ScrollUp
keycode 167 = XF86ScrollDown
```

You can run "xmodmap ~/.Xmodmap" to make that file active.  Now in xev you will notice these keys mapped to XF86ScrollUp and Down, however it seems no applications process these keys.  But if you install the packages xbindkeys and xautomation you can force it to work.  Edit the file ~/.xbindkeysrc to contain:

```
"xte 'mouseclick 4'"
  XF86ScrollUp

"xte 'mouseclick 5'"
  XF86ScrollDown
```

Now run xbindkeys, and add this to your startup applications.  (Make sure xbindkeys is running as a daemon with "pidof xbindkeys", which will return a number if all is well.)  This will use the xte program (installed from the xautomation package) to process every key press of those keys into a mouse button event, which will be processed as if you were using a scroll wheel.

Good luck.

---

### Post by katestange on 2011-02-28
Thank you!  I have found several instances where the scroll wheel acts differently than the arrow keys, so I was really grateful to find this solution.  In particular, the scrollwheel can scroll a webpage without taking focus away from the textbox you're typing in.  It was the Sage notebook ([www.sagemath.org](www.sagemath.org)) that drove me to hunt for this solution.  Thanks again!

---

