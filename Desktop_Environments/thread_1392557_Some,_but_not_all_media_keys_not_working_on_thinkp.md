---
title: "Some, but not all media keys not working on thinkpad r61i"
date: 2010-01-28
forum: Desktop Environments
---

### Post by ireneshusband on 2010-01-28
After installing Kubuntu Karmic I downgraded Amarok to v.1.4 from a PPA and have since upgraded back to v.2.2. Before the downgrade the play control keys (forward, back, play/pause and stop) all worked fine. Now only forward works. I am using a Thinkpad R61i.

I can assign any of those functions (e.g. stop) to the forward media key and it will work. If I assign the forward function to the back, play or stop keys, it will not work. I take this to mean that this is a problem in KDE or elsewhere, and that Amarok is not at fault here.

The problem can't be that the keys have conflicting assignments because KDE control would have complained (but I've checked anyway). So I'm completely at a loss. Anyone got any ideas?

Thanks in advance!

---

### Post by Zorael on 2010-01-29
The system may just not know what the keys mean. If so, that's very fixable by creating a script to run upon login.

If you enter the following in a terminal, does it output anything? (Omit the dollarsign.)
```
$ dmesg | grep atkbd.c
```

---

### Post by ireneshusband on 2010-01-29
Thanks for replying!

dmesg|grep atkbd.c gives me nothing.

I'm not quite clear what you mean about the system just not knowing what the keys mean. I can set the keybindings in the KDE keyboard settings and they will be reported as "media stop" etc. They just don't actually do anything when I try to use them, regardless of whether I assign them to a function in Amarok, in KWin or in anything else.

---

### Post by Zorael on 2010-01-29
Ah, I see. Then yes, the command should output nothing.

Hmm. Could it be the same issue as the Thinkpad r60 has? As per [this thread](http://ubuntuforums.org/showthread.php?t=1328016), try the following;
```
$ sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask
```

The thread discusses it in detail; I only skimmed it. It will only last for the current session, so you'd have to make it be autorun upon boot (with root permissions). If it works.

---

### Post by ireneshusband on 2010-01-29
Thanks once again for your help!

I tried the suggestion, but it didn't work unfortunately.

I've noticed that even though the KDE keyboard controls recognise the keys for what they are supposed to be when I assign them, xev seems confused and can only recognise the audio next key of the four media control keys. Here is what xev tells me, if it helps:

> KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

FocusOut event, serial 32, synthetic NO, window 0x4e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x4e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

FocusOut event, serial 32, synthetic NO, window 0x4e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x4e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

FocusOut event, serial 32, synthetic NO, window 0x4e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x4e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   8   0   0   0   0   0   0   0   0   0   0

KeyRelease event, serial 32, synthetic NO, window 0x4e00001,
    root 0x10b, subw 0x0, time 317181495, (-597,533), root:(501,558),
    state 0x10, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

I should probably emphasise again that it worked for me before, so I am inclined to think that it's not a simple question of faulty support for the platform and probably has something to do with something particular I have done.

---

### Post by Zorael on 2010-01-29
Ugh.

Does it work on another user?

---

### Post by ireneshusband on 2010-01-29
Yes it does. Here is what xev tells me as the other user:

> KeyPress event, serial 31, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328385860, (-694,500), root:(341,525),
   state 0x0, keycode 174 (keysym 0x1008ff15, XF86AudioStop), same_screen YES,
   XLookupString gives 0 bytes:
   XmbLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328385987, (-694,500), root:(341,525),
   state 0x0, keycode 174 (keysym 0x1008ff15, XF86AudioStop), same_screen YES,
   XLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328387000, (-694,500), root:(341,525),
   state 0x0, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
   XLookupString gives 0 bytes:
   XmbLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328387111, (-694,500), root:(341,525),
   state 0x0, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
   XLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328388015, (-694,500), root:(341,525),
   state 0x0, keycode 173 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
   XLookupString gives 0 bytes:
   XmbLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328388174, (-694,500), root:(341,525),
   state 0x0, keycode 173 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
   XLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328389378, (-694,500), root:(341,525),
   state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
   XLookupString gives 0 bytes:
   XmbLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1400001,
   root 0x10b, subw 0x0, time 328389481, (-694,500), root:(341,525),
   state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
   XLookupString gives 0 bytes:
   XFilterEvent returns: False

---

### Post by Newk_77 on 2010-01-30
did you try the package KeyTouch? it solved my problems of non-functioning special keys

---

### Post by ireneshusband on 2010-01-30
I had keytouch already running (although I don't remember installing it). I've tried uninstalling it, but that leaves things exactly the same; The XF86MediaNext key works, but the other three still don't.

---

### Post by Zorael on 2010-01-30
I doubt some package is at fault if it's working as another user. I'm at a loss what could be causing it; I've never had xev spout such nonsense myself.

You could wipe ~/.kde/share/config/khotkeysrc in case something's wrong with it, but I don't imagine that would help. You could also go through your autostart directories (both in .kde and in .config) and make sure you don't have any xmodmap scripts there. (Could KeyTouch have created some?)

Else, you could try to copy your .kde directory to the new user and see if the problem starts occuring. If so you'd know where the error lies, and you're always left with the option to just wipe the directory completely, perhaps backing up specific application configuration files in .kde/share/config and their resources in .kde/share/apps.

---

### Post by ireneshusband on 2010-01-30
The fault is definitely not with Amarok because I can assign the media control keys to KWin actions and run into the same behavour.

I'm tempted just to knock it all on the head because I have discovered that Amarok 2 is still completely broken as far as media devices are concerned, so my upgrade is still a downgrade and I might as well go back to v1.4.

Thanks very much for your help :)

---

### Post by Zorael on 2010-01-30
Amarok 2 doesn't work with later iPod models (iPhone, iPod Touch), but as far as I know it should work as long as the device is properly detected as a media device. Some cheapo media players are detected as normal usb storage, while further others are detected as non-specific "usb devices" (iPhones, iPod Touches).

In the case of misdetected players, the "correct" solution is to add an udev rule to reclassify it. In the case of devices that you need to mount using fuse (iPhones, iPod Touches), there is no solution as of yet because of missing functionality in Solid. Here's to hoping for 4.5.

---

### Post by ireneshusband on 2010-01-31
I've got a generic mass storage device, but I see absolutely nothing in Amarok 2 to do with dealing with it: no settings, no panel, no nothing. This no matter whether I start off with the device mounted or unmounted. Obviously I can still enable it as a "collection", but that leaves me with no way to transfer podcasts, which means that I will have to hope any podcasts I want to listen to have human-friendly filenames so I can find them in Dolphin or Midnight Commander. That's pretty sucky.

---

