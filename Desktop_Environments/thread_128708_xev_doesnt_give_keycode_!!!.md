---
title: "xev doesnt give keycode !!!"
date: 2006-02-12
forum: Desktop Environments
---

### Post by index_0@ya.com on 2006-02-12
hi thr ,
I ran 'xev' utility in my GNOME , but i couldnt find the keycode of my windows key ! . I have Keytouch installed , and it pops out search tool when ever i press Windows key , i want to configure it to Ubuntu menu pop up now .

This is the output i got in xev , i pressed key 'x' and followed by Windows key

"
KeyPress event, serial 26, synthetic NO, window 0x2200001,
    root 0x115, subw 0x0, time 3722868, (593,94), root: 598,167),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: 78) "x"
    XmbLookupString gives 1 bytes: 78) "x"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2200001,
    root 0x115, subw 0x0, time 3723028, (593,94), root:(598,167),
    state 0x10, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"

FocusOut event, serial 29, synthetic NO, window 0x2200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 29, synthetic NO, window 0x2200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ClientMessage event, serial 29, synthetic YES, window 0x2200001,
    message_type 0x11d (_GTK_LOAD_ICONTHEMES), format 32

FocusOut event, serial 30, synthetic NO, window 0x2200001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 30, synthetic NO, window 0x2200001,
    atom 0x14a (_NET_WM_ICON_GEOMETRY), time 3744627, state PropertyNewValue

PropertyNotify event, serial 30, synthetic NO, window 0x2200001,
    atom 0x14a (_NET_WM_ICON_GEOMETRY), time 3744667, state PropertyNewValue

FocusIn event, serial 30, synthetic NO, window 0x2200001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

PropertyNotify event, serial 30, synthetic NO, window 0x2200001,
    atom 0x14a (_NET_WM_ICON_GEOMETRY), time 3747963, state PropertyNewValue

FocusOut event, serial 30, synthetic NO, window 0x2200001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 30, synthetic NO, window 0x2200001,
    atom 0x14a (_NET_WM_ICON_GEOMETRY), time 3817769, state PropertyNewValue

PropertyNotify event, serial 30, synthetic NO, window 0x2200001,
    atom 0x14a (_NET_WM_ICON_GEOMETRY), time 3817779, state PropertyNewValue
"

pls help ...

---

### Post by heimo on 2006-02-12
I don't know if this'll help at all. I don't have any additional hotkey software installed. My "windows key" / "super left" keys's keycode is 115 and menu key (between alt-gr and right ctrl) keycode is 117.

I went to System->Preferences->Keyboard Shortcuts and assigned keys to open Applications menu and new terminal window. Worked without problems, but I also got the events on xev.

---

