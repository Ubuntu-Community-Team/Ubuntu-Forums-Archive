---
title: "after logout and login, up arrow key stopped working in 11.04"
date: 2011-05-05
forum: Desktop Environments
---

### Post by piotrekkr on 2011-05-05
Hi, 

I have quite strange problem with my kubuntu 11.04. Few days ago i found that when I logout from KDE and login again my up arrow key stops working. First I fought that it stopped working only in console but after trying up arrow in few other app effect was the same. When I turn on computer, up arrow works great. It only happens after logout and login again.

This is what xev says when I use up arrow:
```

piotrek@piotrek-desktop:~$ xev
Outer window is 0x3e00001, inner window is 0x3e00002

PropertyNotify event, serial 8, synthetic NO, window 0x3e00001,
    atom 0x27 (WM_NAME), time 935730, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x3e00001,
    atom 0x22 (WM_COMMAND), time 935730, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x3e00001,
    atom 0x28 (WM_NORMAL_HINTS), time 935730, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x3e00001,
    parent 0x3e00001, window 0x3e00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 12, synthetic NO, window 0x3e00001,
    atom 0x19d (_KDE_NET_WM_USER_CREATION_TIME), time 935730, state PropertyNewValue

PropertyNotify event, serial 14, synthetic NO, window 0x3e00001,
    atom 0x114 (WM_PROTOCOLS), time 935730, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x3e00001,
    event 0x3e00001, window 0x3e00002, override NO

ConfigureNotify event, serial 21, synthetic NO, window 0x3e00001,
    event 0x3e00001, window 0x3e00001, (0,0), width 178, height 178,
    border_width 0, above 0x320006a, override NO

ReparentNotify event, serial 21, synthetic NO, window 0x3e00001,
    event 0x3e00001, window 0x3e00001, parent 0x1605ced,
    (0,0), override NO

PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,
    atom 0x13d (_NET_WM_STATE), time 935731, state PropertyNewValue

PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,
    atom 0x1b1 (_NET_WM_DESKTOP), time 935732, state PropertyNewValue

PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,
    atom 0x1a2 (_NET_FRAME_EXTENTS), time 935734, state PropertyNewValue                                                                                                                                                                                                       
                                                                                                                                                                                                                                                                               
PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                               
    atom 0x159 (_KDE_NET_WM_FRAME_STRUT), time 935734, state PropertyNewValue                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                               
PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                               
    atom 0x1b7 (_NET_WM_ALLOWED_ACTIONS), time 935734, state PropertyNewValue                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                               
PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                               
    atom 0x13d (_NET_WM_STATE), time 935735, state PropertyNewValue                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                               
MapNotify event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                                    
    event 0x3e00001, window 0x3e00001, override NO                                                                                                                                                                                                                             
                                                                                                                                                                                                                                                                               
VisibilityNotify event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                             
    state VisibilityFullyObscured                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                               
PropertyNotify event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                               
    atom 0x11b (WM_STATE), time 935735, state PropertyNewValue                                                                                                                                                                                                                 
                                                                                                                                                                                                                                                                               
FocusIn event, serial 21, synthetic NO, window 0x3e00001,                                                                                                                                                                                                                      
    mode NotifyNormal, detail NotifyNonlinear                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                               
KeymapNotify event, serial 21, synthetic NO, window 0x0,                                                                                                                                                                                                                       
    keys:  0   0   0   0   16  0   0   0   0   0   0   0   0   0   0   0                                                                                                                                                                                                       
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0                                                                                                                                                                                                       
                                                                                                                                                                                                                                                                               
ConfigureNotify event, serial 21, synthetic YES, window 0x3e00001,                                                                                                                                                                                                             
    event 0x3e00001, window 0x3e00001, (3,23), width 178, height 178,                                                                                                                                                                                                          
    border_width 0, above 0x0, override NO                                                                                                                                                                                                                                     
                                                                                                                                                                                                                                                                               
VisibilityNotify event, serial 30, synthetic NO, window 0x3e00001,                                                                                                                                                                                                             
    state VisibilityUnobscured

Expose event, serial 30, synthetic NO, window 0x3e00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 30, synthetic NO, window 0x3e00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 30, synthetic NO, window 0x3e00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 30, synthetic NO, window 0x3e00001,
    (0,68), width 178, height 110, count 0

KeyRelease event, serial 30, synthetic NO, window 0x3e00001,
    root 0x15a, subw 0x0, time 935795, (401,918), root:(404,941),
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

PropertyNotify event, serial 33, synthetic NO, window 0x3e00001,
    atom 0x1b4 (_NET_WM_ICON_GEOMETRY), time 936239, state PropertyNewValue

FocusOut event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  68  0   0   0   0   0   0   0   0   0   0   0   0   4294967168 0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x3e00001,
    root 0x15a, subw 0x0, time 939604, (401,918), root:(404,941),
    state 0x10, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyNormal, detail NotifyNonlinear

VisibilityNotify event, serial 34, synthetic NO, window 0x3e00001,
    state VisibilityFullyObscured


```

Any ideas what could be the reason for that?

PS sorry for my poor english

---

### Post by marcgarsan on 2011-08-25
The same problem here. :-(

Heeeeeeelp please!!!!!!!!

I've found [http://fossplanet.com/f12/arrow-keys-wont-scroll-history-squeeze-konsole-bash-20767/](http://fossplanet.com/f12/arrow-keys-wont-scroll-history-squeeze-konsole-bash-20767/) and restart  X server works. It's annoying.

---

