---
title: "Ctrl key gone berzerk"
date: 2007-07-25
forum: Desktop Environments
---

### Post by gorgor_bay on 2007-07-25
I really have a very annoying issue with my production laptop.

The ctrl key has lost its normal behavior, thus all the keybindings are not working properly anymore, and this is a real pain in the *** when one has to do some work done.

The keybindings using ctrl+regular key are not working at all anymore, just there is a change in the cursor when hitting them, which indicates that the ctrl key is still mapped correctly, but has lost its normal behavior.

The kybindings using more that the ctrl key (besides "regular keys) like ctrl+alt+normal key are working in a strange way since I have to hit first alt, then ctrl to get them working.

I am really desperate for help, been keeping asking on the irc forums, google searching and forum searching for more that two days now, and still no answer.

Also the problem is limited to my user account, when I create a new account the problem is not here.

---

### Post by ddrichardson on 2007-07-25
Is there some kind of accessabilty software installed in this account that highlights the mouse when you depress the CTRL key? This would explain why only in one account and why the normal bindings are working when you depress ALT first.

---

### Post by gorgor_bay on 2007-07-25
This starnge behaviour just dissapeared without no further manipulation from my side...

But then, as I was trying to use ctrl+key+arrow to change desktop with the cmpiz fusion cube, at first nothing happened, then I hit "alt+(then)ctrl+arrow" and the cube moved, and after that again no more ctrl+C or ctrl+T in the xterm or firefox or any other ctrl keybinding...

---

### Post by ddrichardson on 2007-07-25
OK, hardware first - is the ALT key next to the CTRL key or are they seperated by a Windows key? Is the keyboard clean, has something worked its way into the membrane?

---

### Post by gorgor_bay on 2007-07-25
The keyboard is a laptop one, there is both a window (super) key and a fn key separating alt and ctrl.
The hardware is okay since the ctrl key is actually working both in kde, in all my other gnome accounts, and eventually in windoze also.

---

### Post by ddrichardson on 2007-07-25
Check the keybindings, press ALT+F2 then:

```
gconf-editor
```

Run it and check under apps for anything with keybindings - Metacity, Compiz, etc.

Then run the followinf command from the terminal:

```
xev
```

This will show you what is happening with different key presses and events.

---

### Post by gorgor_bay on 2007-07-25
I've tried gconf. All the keybindings are properly listed here.
About xev, here is the corresponding output when hitting ctrl :

```
KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4245953975, (166,4), root:(411,217),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4245954195, (166,4), root:(411,217),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

If I hit first ctrl then alt (holding ctrl) I get :

```
KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4246121744, (91,39), root:(451,273),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
```

If I hit first alt then ctrl (holding alt) I get :

```
KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4246158118, (171,6), root:(520,250),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4246158668, (171,6), root:(520,250),
    state 0x8, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4246159259, (171,6), root:(520,250),
    state 0xc, keycode 64 (keysym 0xfe0a, ISO_Prev_Group), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 4246159283, (171,6), root:(520,250),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by ddrichardson on 2007-07-25
There's definately something mapped to CTRL then ALT - what did you find in the bindings?

---

### Post by gorgor_bay on 2007-07-25
The bindings implying CTRL+ALT listed into System>Preferences>Key Bindings are:

[LIST]
[*]Lock screen (ctrl+alt+L)
[*]Move window (shift+ctrl+alt+arrows)
[*]Ctrl+Alt+Tab
[*]Ctrl+Alt+Echap
[*]Ctrl+Alt+D
[*]Ctrl+Alt+arrows
[/LIST]

There's all the classical compiz keybindings, they don't work if they imply only a ctrl key, if it's a ctrl+alt combinaison, then alt has to be pressed first.
I don't know what kind of binding to look for since there are so many of them...
In fact all the kybindings implying more than the ctrl key are working provided the ctrl key is hit in last position before the letter.

---

### Post by ddrichardson on 2007-07-25
Bit of a puzzle this one - CTRL ALT is a different event to ALT CTRL, if its only in this account what have you in use in X thats not in the other account?

---

### Post by gorgor_bay on 2007-07-25
> **ddrichardson said:**
> Bit of a puzzle this one - CTRL ALT is a different event to ALT CTRL, if its only in this account what have you in use in X thats not in the other account?

There are many possibilities as for what is not in use in X in the other account, since the other account is basically empty.
You bet it's a puzzle ! it's now 3 days I'm trying to fix this issue, without success. I guess I'll have to reinstall my system for this stupid error. But I hate to have an error that I cannot solve...

---

### Post by gorgor_bay on 2007-07-25
There's two bugs opened for this issue :
[https://bugs.launchpad.net/ubuntu/+bug/128274](https://bugs.launchpad.net/ubuntu/+bug/128274)
[http://bugs.opencompositing.org/show_bug.cgi?id=30](http://bugs.opencompositing.org/show_bug.cgi?id=30)

---

### Post by ddrichardson on 2007-07-25
Well at least you're getting feedback from other users with the same problem. Hope somenone resolves it soon.

---

