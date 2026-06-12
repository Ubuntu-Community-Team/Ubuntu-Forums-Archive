---
title: "Click locks when both mouse buttons are clicked"
date: 2010-08-10
forum: Desktop Environments
---

### Post by foxten on 2010-08-10
Hi there!

I'm having a *very* annoying problem with Gnome on Ubuntu 10.04.

As I'm an Opera user and like to use mouse gestures, I do a lot of clicking with both mouse buttons to go back or forward on a page. But in this Ubuntu version, when I click both mouse buttons (one after the other, of course), the second clicked button appears to keep clicked. In an example, after going back on a page, when I click a link, the browser do a forward command (because the second button is like being clicked).

I know it is a problem with Gnome because I can reproduce this in the desktop. If you left-click and then right-click at the same time, you can observe that you can't left-click anything on desktop again, only after right-clicking to "release" the right mouse button.

Not a problem of hardware, as this was working on Ubuntu 8.10. No assistive technologies enabled (already enabled then disabled it).

Thanks for the help.

---

### Post by foxten on 2010-08-17
Found out that the problem is in X.
This is the log from 'xev' doing the mouse clicks:

```

-- three clicks with button 1 --

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14740090, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14740218, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14740330, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14740410, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14740530, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14740610, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES


-- three clicks with button 3 --

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14741954, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14742074, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14742138, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14742258, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14742442, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14742538, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES


-- clicking with both mouse buttons, button 1 first then button 3 --

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14743722, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14744370, (110,36), root:(1210,410),
    state 0x110, button 3, same_screen YES

== Here, release both mouse buttons

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14745754, (110,36), root:(1210,410),
    state 0x510, button 1, same_screen YES

== Clicking with button 1 three times

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14746746, (110,36), root:(1210,410),
    state 0x410, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14746874, (110,36), root:(1210,410),
    state 0x510, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14747074, (110,36), root:(1210,410),
    state 0x410, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14747202, (110,36), root:(1210,410),
    state 0x510, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14747362, (110,36), root:(1210,410),
    state 0x410, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14747506, (110,36), root:(1210,410),
    state 0x510, button 1, same_screen YES

== Clicking with button 3 three times

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14748474, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14751474, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14751578, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14751658, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14751794, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

== Again, clicking with button 1 three times

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14752402, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14752482, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14752610, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14752682, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14752786, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14752874, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES


-- clicking with both mouse buttons again, this time first button 3, then 1 --

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14753490, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14753986, (110,36), root:(1210,410),
    state 0x410, button 1, same_screen YES

== Release both buttons

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14754690, (110,36), root:(1210,410),
    state 0x510, button 3, same_screen YES

== Click button 1 two times

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14756354, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14756730, (110,36), root:(1210,410),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14756866, (110,36), root:(1210,410),
    state 0x110, button 1, same_screen YES

== Clicking button 3 two times

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14757378, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14757458, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14758410, (110,36), root:(1210,410),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0x108, subw 0x0, time 14758482, (110,36), root:(1210,410),
    state 0x410, button 3, same_screen YES

```

From this log it can be seen that when both mouse buttons are clicked, the ButtonPress event is registered for both buttons, but when releasing buttons, only one ButtonRelease event is registered, this for the first clicked button.

---

### Post by foxten on 2010-09-22
Hi there,

I'm still with the problem. Anyone out there have reproduced the problem?
Any tips?

Thanks.

---

### Post by nsk7even on 2011-05-16
Hi this topic is a little old but in hope to get a hint:
did you solved this?

For me it is worse:
Normal single left click on the tab preview icons mostly don't let the click release so I accidently do a "drag" with the tab and I have to press ESC to release this drag.

I did so much stuff in the system that I really don't have a clue of where to start searching for a reason for that.

Some customizations:
- disabled Opera internal mouse gestures
- Easystroke mouse gestures to control the whole system (but with right mouse click, not left)
- Various compiz effects and window animation stuff including compiz cube
- Screenlets
- Docky

Any hint?

(Disclaimer: yes I can sequentially go through all those customizations and deactivate them, test, re-activate, but since I am sure there are more than listed above and some issues only disappear after deactivating and restarting e. g. Gnome or the system, this is quite time consuming and I am asking only for some "oh I encountered similar stuff"-thoughts here, not for a complete solution)

---

### Post by foxten on 2011-05-16
> **nsk7even said:**
> Hi this topic is a little old but in hope to get a hint:
did you solved this?


Not yet. I just gave up using the mouse gestures with both clicks. Stupid Gnome and stupid Ubuntu. :mad:

---

