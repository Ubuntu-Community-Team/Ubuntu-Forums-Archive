---
title: "Multimedia keys aren't recognized by xbindkeys"
date: 2009-02-15
forum: General Help
---

### Post by mb_webguy on 2009-02-15
I'm trying to get my laptop's multimedia keys to work with VLC using xbindkeys, as per [this HowTo]("http://www.christiankoller.com/cms/index.php/Allgemein/Software/Control-VLC-via-global-hotkeys-xbindkeys-under-Linux.html").

Well, it doesn't work.

(And before we get any further, Gnome Keyboard Shortcuts recognizes these keys just fine, and I use them in other apps, so it's not a problem with my hardware.)

The problem seems to be that xbindkeys isn't recognizing the multimedia keys *by themselves*.  It *will*, however, recognize them in combination with modifier keys like Shift or Ctrl.  For example, here's the output of "xbindkeys --key" when I press the Ctrl+Play/Pause key combo:```
matt@the-tardis:~$ xbindkeys --key
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x14 + c:172
    Control+Mod2 + XF86AudioPlay

```
No problem, right?  The Play/Pause button is being correctly identified as XF86AudioPlay.  But when I press the Play/Pause button by itself, xbindkeys just sits there as if I haven't pressed anything.

I checked this out with xev, and I'm getting something similar.  If I run xev and then press the Ctrl+Play/Pause button, I get:```
KeyPress event, serial 31, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 222965443, (113,340), root:(1568,394),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 222965641, (113,340), root:(1568,394),
    state 0x14, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 222965762, (113,340), root:(1568,394),
    state 0x14, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x2800001,
    root 0x13b, subw 0x0, time 222966432, (113,340), root:(1568,394),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
This is clearly showing that I pressed Ctrl, then Play/Pause, then released Play/Pause, then released Ctrl.  But when I run xev and just press Play/Pause...```
FocusOut event, serial 31, synthetic NO, window 0x2800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

So, does anyone have any ideas why I'm getting this behavior?  Thanks in advance.

---

### Post by mb_webguy on 2009-02-15
*bump*

---

### Post by cecilx22 on 2009-03-14
try installing and running xbindkeys-config from the repos.  It captures the media keys fine.  Don't know if it'll fix the problem, but it's worth a shot.

Good luck!

---

### Post by mb_webguy on 2009-03-14
Unfortunately, xbindkeys-config is just a front-end for xbindkeys, so if key combo won't work with xbindkeys, it won't work with xbindkeys-config either.  Thanks for trying, though.

I'm still curious about this, if anyone else has any ideas.  Until VLC implements global hotkeys, this is the only way I can think of that I might get my laptop media keys and bluetooth remote to work with VLC, which I use for my default media player... except for when giving a presentation or otherwise want to control playback of a video on my laptop from across the room.

---

### Post by vertago1 on 2010-02-28
Well VLC has the option for global hot-keys in their GUI but it doesn't seem to work. Is it because the implementation isn't there behind the GUI?

This would answer my search for how to get the global hotkeys to work for VLC, Thanks.

---

### Post by runagate on 2011-01-30
For future reference I would suggest removing references to the media keys in the Preferences|Keyboard Shortcuts configuration.

---

### Post by BananusM on 2012-02-19
Yup, removing bindings for media keys from keyboard shortcuts settings makes them visible in xbindkeys.

---

