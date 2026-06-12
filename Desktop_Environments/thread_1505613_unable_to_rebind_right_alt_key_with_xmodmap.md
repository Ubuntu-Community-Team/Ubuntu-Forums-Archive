---
title: "unable to rebind right alt key with xmodmap"
date: 2010-06-09
forum: Desktop Environments
---

### Post by noahlt on 2010-06-09
I am trying to rebind my right Alt key as a Hyper key, so that I can make own keybindings that won't get in the way of my apps/WM.  Unfortunately, I cannot seem to rebind this key.

After freshly logging in, if I run [FONT="Courier New"]xev[/FONT] and press my right Alt key, I get this:

```
KeyPress event, serial 37, synthetic NO, window 0x2200001,
    root 0x13c, subw 0x0, time 50532932, (-1,160), root:(584,211),
    state 0x2000, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x2200001,
    root 0x13c, subw 0x0, time 50533064, (-1,160), root:(584,211),
    state 0x2080, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

But if I run xmodmap to try to rebind the key, it doesn't work:

```
$ xmodmap -e 'keycode 108 = x'
```

Pressing my right Alt key doesn't produce the 'x' character.  Pressing my right Alt key inside of [FONT="Courier New"]xev[/FONT] produces the following:

```
KeyPress event, serial 50, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 51429231, (178,59), root:(184,453),
    state 0x2000, keycode 108 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 50, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 51429452, (178,59), root:(184,453),
    state 0x2000, keycode 108 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

I can use [FONT="Courier New"]xev[/FONT] to find the keycode for my Tab key and rebind it to 'x':


```
$ xmodmap -e 'keycode 23 = x'
```

and then pressing my Tab key results in the 'x' character, but it doesn't work for my right Alt key.

I've Googled and read the man pages, and I still don't know why I can't rebind my right Alt key.  Any ideas?

Thanks in advance!

---

### Post by Brandon Williams on 2010-06-09
The process you used works just fine for me to remap my right Alt key. I notice that your right Alt key produces a different symbol than mine without the mapping. Yours produces ISO_Level3_Shift and mine produces Alt_R. This could be significant, but I'm not sure how. Sorry I can't be more helpful.

---

### Post by humbug01 on 2010-06-09
Your Right-Alt key is set to select the third level key rather than as Alt_R as Brandon noticed. Mine was too and I just changed it in "System > Keyboard > Layouts tab > Options > Key to choose third level" to a different key and now it is Alt_R. Maybe this is the problem?

Best,

Steve

---

### Post by noahlt on 2010-06-10
Thanks humbug01!  Thanks to Brandon, too, for pointing out that my Alt key wasn't producing [FONT="Courier New"]Alt_R[/FONT].

I went to Keyboard Preferences > Layouts > Layout Options and changed "Key to choose 3rd level" to "Right Alt key never chooses 3rd level".  After I restarted my X session, [FONT="Courier New"]xev[/FONT] shows that my right Alt key produces [FONT="Courier New"]Alt_R[/FONT] instead of [FONT="Courier New"]ISO_Level3_Shift[/FONT], which allowed me to add [FONT="Courier New"]Alt_R[/FONT] as a [FONT="Courier New"]Mod3[/FONT] modifier key using [FONT="Courier New"]xmodmap[/FONT].

---

