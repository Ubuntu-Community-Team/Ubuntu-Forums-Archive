---
title: "Alt-Tab key behaviour changes (Gutsy KDE)"
date: 2008-01-27
forum: Desktop Environments
---

### Post by LesleyW on 2008-01-27
Hi all,

**Environment:**
I'm running a fairly standard KDE environment on Gutsy, and I have just run an update so my packages are all at the latest version as of today.  Normally, ie after a reboot, Alt-Tab behaves the same as in Windows, and that's how I like it.

**The problem**
Every so often, apparently at random, the Alt-Tab key mapping gets messed up somehow, and instead of switching widows I get a bizarre little pop-up that says "it seems that Kmix is not running" (I've uninstalled Kmix, it still happens). Actually, this happens as soon as I hit the Alt key, which means there's no change of actually getting to the Alt-Tab combo. I can't find any way to put it back to normal other than restarting X which I really hate doing as it really messes up my day.

How can I figure out what's going on here? And how can I prevent it?

**More info**
I don't use any sound system stuff, as this is a work environment, and it doesn't seem to work properly anyway. I've never installed any extra sound-related packages. I cannot isolate any particular trigger that causes this behaviour change, it just happens while I'm working, The things I normally have running are Konsole (lots of them), Firefox (usually several), VMWare Workstation, and a couple of X utilities that are not sound-related.

The output below is from xev when I press and release the Alt key. It would appear that the "KeyRelease Event" is the relevant part, but I have no idea what to do next with this information.

Hardware is Dell Optiplex 755, if that's relevant.

```

FocusOut event, serial 32, synthetic NO, window 0x1000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x1000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   64  0   0   0   0   0   0   0   0   0   0

KeyRelease event, serial 32, synthetic NO, window 0x1000001,
    root 0x5c, subw 0x0, time 3183470368, (49,-4), root:(52,968),
    state 0x10, keycode 174 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

VisibilityNotify event, serial 32, synthetic NO, window 0x1000001,
    state VisibilityPartiallyObscured

VisibilityNotify event, serial 32, synthetic NO, window 0x1000001,
    state VisibilityUnobscured

Expose event, serial 32, synthetic NO, window 0x1000001,
    (70,8), width 88, height 21, count 0

VisibilityNotify event, serial 32, synthetic NO, window 0x1000001,
    state VisibilityPartiallyObscured

VisibilityNotify event, serial 32, synthetic NO, window 0x1000001,
    state VisibilityUnobscured

Expose event, serial 32, synthetic NO, window 0x1000001,
    (91,1), width 65, height 21, count 0

VisibilityNotify event, serial 32, synthetic NO, window 0x1000001,
    state VisibilityPartiallyObscured

VisibilityNotify event, serial 32, synthetic NO, window 0x1000001,
    state VisibilityUnobscured

Expose event, serial 32, synthetic NO, window 0x1000001,
    (120,0), width 58, height 18, count 0

FocusOut event, serial 32, synthetic NO, window 0x1000001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 32, synthetic NO, window 0x1000001,
    atom 0x18b (_KDE_WM_WINDOW_OPACITY), time 3183490569, state PropertyNewValue


```

---

### Post by LesleyW on 2008-02-27
Bump... I still need help with this, is there anyone out there who can help me figure out what to try next?

The only additional info I can add is:
[LIST]
[*]It has taken 30 days from the last reboot for it to happen again
[*]I have run the following things today that I don't usually run:[LIST]
[*]GIMP
[*]GwenView
[*]Dolphin
[/LIST]
[*]Apart from that, I have done nothing out of the ordinary today that I wouldn't have done every other day
[*]System Guard tells me my system is busy, but not overloaded
[/LIST]

---

