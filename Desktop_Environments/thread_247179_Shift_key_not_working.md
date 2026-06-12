---
title: "Shift key not working"
date: 2006-08-30
forum: Desktop Environments
---

### Post by ElVirolo on 2006-08-30
Hi all,

I'm using a French AZERTY keyboard on Ubuntu Dapper, and the Shift key, as well as the F*n* (where *n* is a number between 1 and 12) keys don't work...
I tried running **dpkg-reconfigure xserver-xorg**, but it still doesn't work ...

Here is the "keyboard" section of my /etc/X11/xorg.conf :

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "fr"
EndSection
```

Many thanks,

Alex.

---

### Post by bukwirm on 2006-08-30
Run the xev command, press one of the F*n* keys, and post the last paragraph of output. It should look something like this:
```
KeyRelease event, serial 30, synthetic NO, window 0x1600001,
    root 0x4c, subw 0x0, time 1601646612, (-33,-93), root:(611,92),
    state 0x10, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
```

---

### Post by ElVirolo on 2006-08-30
Here's the output when I press an F key (or indeed, shift) : 

```
KeyRelease event, serial 32, synthetic NO, window 0x1400001,
    root 0x4c, subw 0x0, time 1604049851, (-302,731), root:(796,817),
    state 0x10, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes:

```

Thanks for you help,

Alex.

---

### Post by bukwirm on 2006-08-30
So when you press F1 in an application (firefox for example), nothing happens? And if you press shift + [any letter] you get a lowercase letter?

---

### Post by ElVirolo on 2006-08-30
Sorry, in fact, the F keys do indeed work properly.
However, when I use the shift key, I do get a lower case letter - and the same applies for other characters, such as ","...

---

### Post by ElVirolo on 2006-08-30
Any ideas?

Thanks in advance,

Alex.

---

### Post by bukwirm on 2006-08-30
What result do you get when you run xev and press shift?

---

### Post by ElVirolo on 2006-08-30
This is what I get :

```
KeyPress event, serial 29, synthetic NO, window 0x1400001,
    root 0x4c, subw 0x0, time 1611321504, (715,460), root:(719,546),
    state 0x10, keycode 50 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x1400001,
    root 0x4c, subw 0x0, time 1611321551, (715,460), root:(719,546),
    state 0x10, keycode 50 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
```

Thanks for your help.

---

### Post by bukwirm on 2006-08-30
Ok, try this:
1. make a file called .xmodmaprc in your home directory
2. add these lines to the file

```
keycode **[keycode_l]**=Shift_L
keycoed **[keycode_r]**=Shift_R
```

where **[keycode_l]** and **[keycode_r]** are the keycodes produced by xev when you press the left and right shift keys (in bold): ```
KeyRelease event, serial 32, synthetic NO, window 0x1400001,
    root 0x4c, subw 0x0, time 1611321551, (715,460), root:(719,546),
    state 0x10, keycode **50** (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
```

3. Add this line to your .xsession file:
```
xmodmap .xmodmaprc
```

EDIT2 4. Restart X Windows by pressing Ctrl+Alt+Backspace.



EDIT: There may be a better way to do this, but I don't know it.

---

### Post by ElVirolo on 2006-08-30
The thing is that accents don't work either ...

Thank you for your help.

---

