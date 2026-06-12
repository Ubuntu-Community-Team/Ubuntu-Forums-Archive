---
title: "Remap Keyboard Keys"
date: 2005-12-20
forum: Desktop Environments
---

### Post by Gandalf on 2005-12-20
Hello

On my keyboard (French Keyboard aka azerty) the key (<>) is broken (it doesn't work not ubuntu fault it's just a dead button) so i would like to replace the left Windows logo key with this one, is that possible to do?

Thanks

---

### Post by frodon on 2005-12-20
Yes you can.
Run "xev" and press the key you want to use and get its keysim, exemple of a xev output : ```
KeyRelease event, serial 26, synthetic NO, window 0x3e00001,
    root 0x46, subw 0x0, time 521316987, (205,196), root:(209,222),
    state 0x50, **keycode 115** (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:  ""

FocusOut event, serial 26, synthetic NO, window 0x3e00001,
    mode NotifyNormal, detail Notify
```Then run this command to map the key : ```
xmodmap -e "keycode xx = less greater"
```Add this command in the "startup session commands" or in your .bashrc to do it automatically.

---

### Post by Gandalf on 2005-12-20
Thanks man that worked like a charm...

---

### Post by rjz35 on 2007-02-10
I've got with my dell d620 an tagrus keypad, it is functioning, only the "/" "*" "-" "+" are not working, i tried xmodmap  them, but got.

xev gave.

KeyPress event, serial 32, synthetic NO, window 0x4200001,
    root 0x52, subw 0x4200002, time 2899000130, (64,64), root:(74,93),
    state 0x10, keycode 112 (keysym 0x1008fe20, XF86_Ungrab), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4200001,
    root 0x52, subw 0x4200002, time 2899000258, (64,64), root:(74,93),
    state 0x10, keycode 112 (keysym 0x1008fe20, XF86_Ungrab), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

 xmodmap -e "keycode 112 = +"
xmodmap:  commandline:1:  bad keysym name '+' in keysym list
xmodmap:  1 error encountered, aborting.

after this i did xmodmap -pk which gave me this.

112         0xffaf (KP_Divide)      0x1008fe20 (XF86_Ungrab)


does anybody has any idea.

thanks already.
:(

---

### Post by celsofaf on 2007-02-21
I have a similar issue as the original poster, and partialy solved my problem. The only thing I need to know is the "name" of the ¦ key; it was copied-pasted here, because I need to remap it elsewhere. The "name" of < would be "less greater"; what would be the name of ¦ ? I googled for it without success, and tried stuffs like "vertical bar", "broken bar", "pipe" without success.

:/

---

### Post by celsofaf on 2007-02-21
Nevermind, I found it out: it's simply "bar".

---

### Post by RedSquirrel on 2007-02-22
> **rjz35 said:**
> I've got with my dell d620 an tagrus keypad, it is functioning, only the "/" "*" "-" "+" are not working, i tried xmodmap  them, but got.

xev gave.

KeyPress event, serial 32, synthetic NO, window 0x4200001,
    root 0x52, subw 0x4200002, time 2899000130, (64,64), root:(74,93),
    state 0x10, keycode 112 (keysym 0x1008fe20, XF86_Ungrab), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x4200001,
    root 0x52, subw 0x4200002, time 2899000258, (64,64), root:(74,93),
    state 0x10, keycode 112 (keysym 0x1008fe20, XF86_Ungrab), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

 xmodmap -e "keycode 112 = +"
xmodmap:  commandline:1:  bad keysym name '+' in keysym list
xmodmap:  1 error encountered, aborting.

after this i did xmodmap -pk which gave me this.

112         0xffaf (KP_Divide)      0x1008fe20 (XF86_Ungrab)


does anybody has any idea.

thanks already.
:(

Instead of 

```
xmodmap -e "keycode 112 = +"
```try

```
  xmodmap -e "keycode 112 = KP_Add"
```

---

### Post by RedSquirrel on 2007-02-22
> **frodon said:**
> 

Then run this command to map the key :      
     [LEFT]```
xmodmap -e "keycode xx = less greater"
```[/LEFT]
 
Add this command in the "startup session commands" or in your .bashrc to do it automatically.


Or you can create the file ~/.Xmodmap and put all of your xmodmap commands in there. They will be run automatically. 

If you put commands in that file, you won't need the xmodmap command for each line, just something like this:

```
keycode 112 = KP_Add
```

---

### Post by mlissner on 2007-02-23
There's a way to figure out these keysys things for other buttons. Install xkeycaps. It'll fix ya right up with the correct ones. I am annoyed because had I not figured that out, I would have NEVER figured out that backspace is properly called BackSpace.

I just ran xmodmap -e "keycode 66 = BackSpace"

Which makes my caps lock behave as a backspace button...though it's still turning on and off the caps lock function for the moment.

EDIT - Ok, easy fix for that - Forget the command line, open xkeycaps, rightclick and hold down the key on the caps lock key, and select edit keysyms of key. Turn on autorepeat, turn off lock. Now...will this be here next time I restart? Probably not. Indeed, no, it isn't functioning upon reboot...hmmm...

---

### Post by Big_Rog on 2007-03-03
How would I go about remapping the keys on a second keypad?  I have a Belkin Nostromo n52 speedpad, and it currently generates key codes starting in the upper left corner of the keyboard, i.e.

[TAB] Q W E R
[CAPS_LOCK] A S D F
[SHIFT_L] Z X C

There are plenty of open slots in the upper registers (ran xmodmap -pke) to assign with unique names, perhaps in the N52[#] theme, i.e. N52_1, N52_2...N52_*n*.

I've just tinkered with my xorg.conf to get my MX700 functioning as intended and having been successful with that, I'm feeling brave enough to tackle this next challenge.  From what I've seen with xmodmap, it only affects ALL keycodes, not keycodes from a specific device.

Would it be possible to identify the keypad by event# in the xorg.conf, and give it a different language layout, then xmodmap only keys on that language?  Perhaps I'm trying to use xmodmap in a way it wasn't intended.  Then again, how many computers have you ever known to use more than one keyboard?

Would this pretty much require a driver to intercept the keycodes at the USB port and generate different codes?  Is it possible to make a new 'foreign' keyboard layout that only uses higher range codes?  So many questions...

---

### Post by Big_Rog on 2007-03-03
OK, after running xkeycaps, the n52 is indeed generating what the system believes to be keypresses from the main keyboard.  Remapping the keysyms in xkeycaps is not what i want to do, because that will break the main keyboard.  I attempted to get a copy of the n52 driver from sourceforge, but due to the outdatedness of it, the make/compile didn't work, and it looks like noone has tinkered with it in a long time...

---

### Post by Big_Rog on 2007-03-03
Hmm, according to the README in /etc/X11/xkb/compat:

> The core protocol interpretation of keyboard modifiers does not include direct
support for multiple keyboard groups, so XKB reports the effective keyboard
group to XKB-aware clients using some of reserved bits in the state field of
some core protocol events. This modified state field would not be interpreted
correctly by XKB-unaware clients, so XKB provides a group compatibility mapping
which remaps the keyboard group into a core modifier mask that has similar
effects, when possible.

 I.e. X server lumps all keyboard input into one single grouped output?  This isn't the end of the world, I just need to find a way to map the keys on the n52 to the unused regions of my keyboard.  Is it possible to create my own xkbRules, xkbModel, and xkbLayout?

---

### Post by glenmo on 2007-05-06
i'm in the same boat -- i'm also not afraid of xorg.conf but i don't really know how to start editing it for this kind of thing... i tried the drivers on sourceforge too, same result as you... 

find anything for this on your own?  i'll post anything i find...

---

### Post by LordVeovis on 2008-04-24
I would like to know if it is posible as well.  I have a N52 on 64 bit Ubuntu... so I have no drivers at all, not even old ones.

---

### Post by mbutu on 2008-07-12
I have the same problem of a dead key
Shift key is dead, so I tried
 
 xmodmap -e "keycode 115 = Shift_L"

nothing. then tried

 xmodmap -e "keycode 115 = Shift_R"

nothing again. then

 xmodmap -e "keycode 115 = EuroSign"

it worked. But my problem is shift key.
thank you in advance

---

