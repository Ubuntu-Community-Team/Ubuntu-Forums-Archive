---
title: "Volume up-down keys in XFCE (Xubuntu)"
date: 2007-06-08
forum: Desktop Environments
---

### Post by Stokky on 2007-06-08
I searched around and found several people trying to figure out how to set shortcuts for the special multimedia keys (e.g. volume up-down / mute), which don't seem to be recognized by XFCE by default.

I found the solution over here: [http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/](http://alvonsius.wordpress.com/2007/01/08/xfce-volume-controlling-with-keyboard/)

> Little googling I found out that using amixer could resolve this. Here it goes &#8230;

First you must know the basic command of amixer (this is myown simplified version) :

amixer [command] [control] [parameter] &#8230;. more read here (or just read the manual)

To be used for my need I use this three command :

**amixer set Master 5+** : increase the volume by 5

**amixer set Master 5-** : decrease the volume by 5

**amixer set Master toggle** : switch between mute and unmute volume

Okay, after that go to Settings >  Keyboard Settings, pick the Shortcuts tab and add your own Themes by clicking the (+ Add) button at the theme list. After that, just add those three command to the shortcut list (I don&#8217;t have to write the howto here since the steps from the application is preety much helping).

Done, now I can control my volume trough keyboard. Humm, I wonder when will I stop using xfce now &#8230;. ^^

It might work better if you set "0.1+/-" instead of "5+/-" in those commands.

---

### Post by diatribe on 2007-06-08
I noticed that when using xfce on my acer laptop, the volume up/down keys only work if you add the volume panel applet.  might work for you also dunno

---

### Post by bapoumba on 2007-06-09
May be you found a solution already.
Did not run into that problem myself. I have the xfce4-mixer applet running, and the <Fn><F8 or F9> keys properly working (replace F8 or F9 with the proper keys for your keyboard).

---

### Post by MatthewPlanchard on 2007-10-20
Hey, I don't know if you've already solved this, but I found a solution in case anyone is still having this problem.

go to system->synaptic packet manager and install the following package:

xfce-xfapplet-plugin

It'll allows you to add GNOME deskbar applets to your panel. Just add the volume control and, as long as your volume works natively in GNOME, you'll be ready to go!

---

### Post by zlO_Olz on 2007-10-20
In feisty i was able to control volume up/down & mute with keys Fn+F10/F11/F12, now after updating to gutsy the "Fn" key doesn't seem to work anymore (I noticed this trying to configure shortcuts in keyboard preferences)

Does anyone know how to solve this? I have an asus a6g laptop with xubuntu 7.10

thank you

---

### Post by johnxx on 2007-10-21
I have the same problem and I am working on it. xev tells me that the keycodes for my multimedia keys aren't associated with any keysyms. Could you run xev from a terminal and then press one of your multimedia keys that doesn't work? Does it give output similar to this:
```
KeyRelease event, serial 27, synthetic NO, window 0x4c00001,
    root 0xc1, subw 0x0, time 3239744614, (-835,221), root:(494,279),
    state 0x0, keycode 162 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
The part I'm interested in is the "keysym 0x0, NoSymbol"

If yours looks like that too, you're probably having the same problem as me.

-John

---

### Post by johnxx on 2007-10-21
I grabbed this from the Gentoo - "Howto use multimedia keys" ( [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Setting_up_xmodmap](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Setting_up_xmodmap) )

Make a file in your home directory called .xmodmap and paste this into it:
```

keycode 222 = XF86PowerOff
keycode 223 = XF86Sleep
keycode 236 = XF86Mail
keycode 229 = XF86Search
keycode 230 = XF86Favorites
keycode 178 = XF86WWW

keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 160 = XF86AudioMute
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume

```

EDIT: After that run xmodmap .xmodmap from your home directory, then try using the keys and/or trying binding them to something in the XFCE keyboard shortcuts program.

There seems to be a fairly standard mapping here, since this lists the same mappings as my notebook has. If this doesn't work for you, you might want to try digging through the part of the gentoo howto I linked, as it has good information. 

If you feel like all of this is over your head, then just wait and I'm sure it will get fixed soon in an update. :D

-John

EDIT: I should really test this stuff before I hit reply. :/

---

### Post by zlO_Olz on 2007-10-21
> **johnxx said:**
> Could you run xev from a terminal and then press one of your multimedia keys that doesn't work?

[LIST]
[*]just Fn: nothing happens :(
[*]Fn+F10, Fn+F11, Fn+F12: same result for all combinations
```

FocusOut event, serial 30, synthetic NO, window 0x2e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x2e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```
[*]F10, F11, F12
```

KeyPress event, serial 28, synthetic NO, window 0x3000001,
    root 0x5b, subw 0x0, time 3256386698, (-282,164), root:(269,472),
    state 0x0, keycode 76 (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x5b, subw 0x0, time 3256386779, (-282,164), root:(269,472),
    state 0x0, keycode 76 (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x5b, subw 0x0, time 3256387552, (-282,164), root:(269,472),
    state 0x0, keycode 95 (keysym 0xffc8, F11), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x5b, subw 0x0, time 3256387638, (-282,164), root:(269,472),
    state 0x0, keycode 95 (keysym 0xffc8, F11), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x5b, subw 0x0, time 3256388069, (-282,164), root:(269,472),
    state 0x0, keycode 96 (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x5b, subw 0x0, time 3256388145, (-282,164), root:(269,472),
    state 0x0, keycode 96 (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
[/LIST]

---

### Post by zlO_Olz on 2007-10-22
This is my /proc/acpi/asus listing:

```
:/proc/acpi/asus$ ls

brn  disp  info  lcd  mled  wled

```

these should configure my Fn keys for brightness (brn) etc. I suppose... but there's nothing related to volume controls :(
should I have to install something in particular?

please help!

---

### Post by wersdaluv on 2007-10-23
Same here. The Fn key does not work as a modifier on Gutsy if I set keyboard shortcuts. In Feisty, Fn worked.

---

### Post by VicAlpha on 2007-10-23
I've solved all my fn keys problems with Keytouch

---

### Post by khristian on 2007-12-04
I came to this thread looking for a way to enable the Fn+up/down volume control keys on my acer notebook. Turns out that Xfce uses very small values for each keypress (like the +0.1 mentioned before), so I have to press the combination a few times before I notice any change. 
:P

edit: Here I am again, for my other keys (Fn+Play/Pause/etc) don't work.
The trick is, these keys work with Exaile, for example, but not for Amarok. So, if anyone knows which package makes it work from the KDE set, please let me (and us) know, thanks!

---

