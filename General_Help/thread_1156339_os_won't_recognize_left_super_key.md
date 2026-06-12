---
title: "os won't recognize left super key"
date: 2009-05-11
forum: General Help
---

### Post by sideffects on 2009-05-11
My right super key works just fine. I've also tested both of my super keys using the terminal, and the it doesn't recognize the left super key. Thanks in advance.

---

### Post by Wiebelhaus on 2009-05-11
It's not a super key , it's a windows key which I don't recognize either.

I'm joking!

You can specify it's action in keyboard shortcuts.

---

### Post by AndThenWhat on 2009-05-11
I would go under (System -> Preferences -> Keyboard) and play around with those settings. Under the Layouts tabs I clicked the Layout Options button and it has configuration for the Alt/Win key behavior.

If that doesn't work you may need to change your keyboard layout to something other than the current setting.

---

### Post by sideffects on 2009-05-11
Yeah, it was working for a while, but it recently stopped and I have no idea why. I did play around with the alt/win settings some.

---

### Post by Wiebelhaus on 2009-05-11
Like I said you can set it to anything you want in Keyboard shortcuts , check screenie.

---

### Post by sideffects on 2009-05-11
Oh, sorry I misunderstood. Thank you very much!

---

### Post by Wiebelhaus on 2009-05-11
> **sideffects said:**
> Oh, sorry I misunderstood. Thank you very much!

No worries mate.

---

### Post by sideffects on 2009-05-11
wait, wait. I can't assign the left super key in keyboard shortcuts.

EDIT: The "L Super" key shows up as "Mod4" in keyboard shortcuts. Why is that?

---

### Post by sideffects on 2009-05-12
bump

---

### Post by AndThenWhat on 2009-05-15
Mod4 is just how the computer recognizes the left super key. The right super key is probably Mod5.

---

### Post by 1jackjack on 2009-05-24
@sideffects I was having trouble with this exact same problem, and I tried changing the keyboard setting as mentioned above, and then Keyboard Shortcuts wouldn't take the win key as a key on it's own, and when I tried win key and a letter, it appeared as Mod4 and that letter (and the shortcut didnt work).

Ultimately, I went back to those keyboard settings, and changed 'Alt/Win key behavior' back to default, then Keyboard Shortcuts accepted my win key again, as a shortcut, all on it's own (It came up as Super_L again, just like it used to), then it worked.

I think what was causing my problem was messing around with different compositing managers (metacity and compiz). Try disabling compiz (menu>system>prefs>appearance>visual effects>none) and disabling metacity compositing with the following command:
gconftool-2 --set --type=bool /apps/metacity/general/compositing_manager false

then restart, then set 'Alt/Win key behavior' back to 'default' and try setting a keyboard shortcut to just win key, and see if it works... (btw, i'm assuming you're using the hotkey manager in menu>system>prefs>keyboard shortcuts, as this is what worked for me)

EDIT: after setting a new command to Super L, it didn't work immediately. I had to do a bit of fiddling to get it actual working: try closing and re-opening the keyboard shortcuts window. try double clicking the entry in keyboard shortcuts (for custom shortcuts, this brings up the name/command dialogue, where you should just press apply). try setting the shortcut to <Ctrl>Super L and getting that working, then setting it to just Super L. A combination of these seemed to get mine working... good luck!

---

### Post by sideffects on 2009-05-25
Yeah, I basically did the same thing you did before i read your post. Guess fiddling works, too.

---

### Post by pjalegria on 2009-10-01
Didnt work for me :(

---

### Post by pjalegria on 2009-10-01
xev outpot:

> KeyPress event, serial 34, synthetic NO, window 0x4a00001,
    root 0x104, subw 0x0, time 1166720, (726,-14), root:(726,11),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


cant someone help me please???

---

### Post by pjalegria on 2009-10-02
bump

---

