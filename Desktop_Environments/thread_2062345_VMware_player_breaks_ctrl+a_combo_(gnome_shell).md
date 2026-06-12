---
title: "VMware player breaks ctrl+a combo (gnome shell)"
date: 2012-09-24
forum: Desktop Environments
---

### Post by neerolyte on 2012-09-24
I keep losing the ctrl+a key shortcut in Ubuntu 12.04 with Gnome shell currently.

It seems to mostly happen after running a VM in VMware player, however even after closing it (and then killing off all remaining processes, halting both vmware services under /etc/init.d and ensuring nothing remains by using "ps aux") I still can't use ctrl+a in any windows (e.g. terminals when using GNU screen or text editors).

Testing with xev I see some 2xFocusOut, FocusIn and KeymapNotify events where there should be the KeyPress and KeyRelease events:
```

KeyPress event, serial 32, synthetic NO, window 0x3200001,
    root 0xcc, subw 0x0, time 81930885, (57,2), root:(1785,193),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 32, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 32, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 32, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  4294967244 0   0   0   32  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0xcc, subw 0x0, time 81932126, (57,2), root:(1785,193),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

... which just seems odd.

I can reliably fix the problem by rebooting (not good enough!).

The "a" key still works on its own, as does "ctrl+shift+a", "shift+a", "alt+a" and modifier keys used with other letters - it's just "ctrl+a" that seems to break.

Can anyone give me any pointers about where else to look?


Cheers,
Dave

---

### Post by rockorequin on 2012-12-02
When using VMwarePlayer in Unity, I lose CTRL-everything. Do you lose just CTRL-a in gnome-shell?

Running setxkbmap fixes it for me temporarily, but only until the mouse cursor goes back over the VMwarePlayer window. I guess VMwarePlayer grabs the keyboard when you cursor-over its window, but fails to release it correctly when you leave its window, ie it continues intercepting the CTRL key.

Did you ever figure out a more permanent fix? I tried the fixes suggested at [http://nthrbldyblg.blogspot.com.au/2008/06/vmware-and-fubar-keyboard-effect.html](http://nthrbldyblg.blogspot.com.au/2008/06/vmware-and-fubar-keyboard-effect.html), but they didn't work.

VMWare has had problems with the keyboard for many years now (eg see [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/195982)), so I guess integrating properly with Linux hosts is very low on VMware's agenda.

---

### Post by rockorequin on 2012-12-02
And then I remembered I have gnome-shell installed, so I can try it. In Ubuntu 12.10 with vmwareplayer 5, I lose CTRL-everything as well when vmwareplayer is running. I also lose the ability to type the 'm' key (shift-m works, but not 'm') because it brings up the gnome-shell bottom status bar instead of typing m.

setxkbmap fixes it temporarily in gnome-shell, but this bug does render vmwareplayer pretty much unusable.

---

### Post by neerolyte on 2012-12-02
Nah I was just losing "Ctrl+a" (in all apps, e.g. select all in gedit as well). All other modifier keys worked.

My permanent fix was to get rid of VMWare Player.

---

### Post by rockorequin on 2012-12-02
> **neerolyte said:**
> 
My permanent fix was to get rid of VMWare Player.

Yup, that's what I did back in 2008. :)

fwiw, I found the source of my problem. xmodmap showed:

```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3        Control_R (0x69)
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)


```
Another user on my system had the same modmap, but mod3 was blank. vmplayer worked fine for the other user, but for my user vmplayer was clearing everything, so that xmodmap showed:

```
shift     
lock      
control   
mod1      
mod2      
mod3      
mod4      
mod5    

```


After issuing xmodmap -e "clear mod3", vmplayer worked fine for my user as well (including for CTRL-A).

---

