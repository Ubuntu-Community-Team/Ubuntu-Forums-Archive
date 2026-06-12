---
title: "previous next page special keyboard keys - howto"
date: 2006-10-03
forum: Desktop Environments
---

### Post by lptr on 2006-10-03
Is it possible to configure previous next page keys on keyboard to be linked to key combination alt-left/right keys under KDE?

I'm using a Thinkpad z60m. IBM keyboards usually having those two special keys located in keyboard cursor block.


rob*

---

### Post by lptr on 2006-11-15
[update]
maybe I was somewhat to unspecific what I want. 

The plan was to activate these two special keys on IBM keyboard (located directly left and right of cursor up key) in Firefox to quickly navigate to the previous side in history or to next side already visited before. Yes of course one could press the key combination alt-left(cursor) and alt-right instead, but it is sometimes of value reaching this directly with one keystroke.

Inbetween I found a working solution myself which may be of value for others, too. The only point I don't understand right now is why mimiking alt-left and alt-right instead of <back> and shift<back> does not work. Maybe anybody can help here with an answer? I will mention this some later in code.


There were three steps necessary to bring the keys to work.

+ detecting if keystrokes are recognized by X
+ modifying xmodmap
+ changing xkb/compat


Detection:

Ok, howto recognize pressed keys?
# xev
 pressing prevPage will output this:
```

KeyPress event, serial 31, synthetic NO, window 0x4400001,
    root 0x76, subw 0x0, time 3945456576, (165,-14), root:(843,807),
    state 0x0, keycode 234 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x76, subw 0x0, time 3945456576, (165,-14), root:(843,807),
    state 0x0, keycode 234 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:

```
Pressing nextPage returns a keycode of 233.


lshal shows this when pressing pageleft and then pageright:
```
# lshal -m

Start monitoring devicelist:
-------------------------------------------------
platform_i8042_i8042_Kbd_Port_logicaldev_input condition ButtonPressed = back
platform_i8042_i8042_Kbd_Port_logicaldev_input condition ButtonPressed = forward

```


---
xmodmap
---
here is a more detailed description what can be done beyond that what I did:
[http://www.tannerstokes.com/2006/08/02/getting-those-multimedia-keys-to-work-in-kubuntu/](http://www.tannerstokes.com/2006/08/02/getting-those-multimedia-keys-to-work-in-kubuntu/)

In short:
```
# cd ~
# xmodmap -pke > xmodmap.conf
# kate xmodmap.conf

```
find and modify 
```
keycode 233 = XF86Forward
keycode 234 = XF86Back

```

```
# cd ~/.kde/Autostart
# touch keyboardmap
# kate keyboardmap

```
fill this file with these two lines:
```
#!/bin/sh
xmodmap /etc/xmodmap.conf
```

save that and make it runable:
```
# chmod +x keyboardmap
```


---
xkb/compat modification
---
```
# sudo nano /etc/X11/xkb/compat/ibm_z60m
```

fill following into it:

```
// $XFree86$
//  XFree86 special keysyms

default partial xkb_compatibility "basic"  {

    interpret.repeat= True;

//  Backspace for Back (Firefox)
    interpret  XF86Back {
        action = Redirect(Key=<BKSP>);
    };

//  Shift+Backspace for Forward (Firefox)
    interpret  XF86Forward {
        action = Redirect(Key=<BKSP>, modifiers=Shift);
    };
};
```

safe content

now 
```
# sudo nano /etc/X11/xkb/compat/complete
```

adding line 
```
augment "ibm_z60m"
```

between brackets. Here on this machine the file looks like this:

```

// $XKeyboardConfig: xkbdesc/compat/complete,v 1.3 2005/10/17 00:42:11 svu Exp $
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete"  {
    include "basic"
    augment "iso9995"
    augment "mousekeys"
    augment "accessx(full)"
    augment "misc"
    augment "xfree86"
    augment "level5"
    augment "ibm_z60m"
};

```

restart machine (or X whatever one likes more).

Now the PageLft/Rght of IBM keyboard should be translated into Backspace or Shift-Backspace.


:-k SIDENOTE: Instead of
```
        action = Redirect(Key=<BKSP>);
        action = Redirect(Key=<BKSP>, modifiers=Shift);
```
I tried this
```
        action = Redirect(Key=<KP_Left>, modifiers=Alt_L);
        action = Redirect(Key=<KP_Right>, modifiers=Alt_L);
```
but had no success. ((Any ideas?))
SIDENOTE END:

---

