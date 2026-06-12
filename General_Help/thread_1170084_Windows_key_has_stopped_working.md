---
title: "Windows key has stopped working"
date: 2009-05-25
forum: General Help
---

### Post by zeug on 2009-05-25
I have tried the suggestion of setting the option "Super is mapped to Win keys" and it still has not fixed the problem.  I also have Openbox installed and it does not work there either.  The windows keys did work originally but after playing around with Openbox earlier (rc.xml and menu.xml) it stopped.  After a reboot the problem is still there.  The keyboard layout I have is "Generic 105-key (intl)".  Thanks, zeug.

---

### Post by zeug on 2009-05-25
I have found out that the shortcuts work with the Fn key and Windows key instead of just the Windows key.

How can I fix it so that it is just Windows key?

Thanks,
zeug.

---

### Post by Steelmourne on 2009-05-25
Try getting rid of openbox as windows manager and returning to ubuntu's defaults. Then try compiz fusion.

---

### Post by zeug on 2009-05-25
Openbox is not my windows manager in GNOME, it is used as a desktop environment by itself.

What do I try in Compiz?

zeug.

---

### Post by zeug on 2009-05-26
Bump before it gets this gets lost.  I have tried to Google my the 'new' question but it still does not yield results.  zeug.

---

### Post by zeug on 2009-05-28
Bump. Anyone have an idea of how to remap the Windows key so it can be used without the FN key?

---

### Post by zeug on 2009-05-29
This is the output of xev when Windows and Fn are pressed and released.
```
KeyPress event, serial 35, synthetic NO, window 0x3800001,
    root 0x13c, subw 0x0, time 1193134, (744,376), root:(747,425),
    state 0x10, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3800001,
    root 0x13c, subw 0x0, time 1193286, (744,376), root:(747,425),
    state 0x50, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

This is the output of just the Windows key when pressed and released.
```

FocusOut event, serial 35, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 35, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

Anyone know how to fix it?

zeug.

---

### Post by s.fox on 2009-05-29
Hi,

I had a problem with the letter "a" key not working either.  I found compiz-fusion had been using it as a short cut for one of my effects.  I went through and checked each display effect and checked out all the keyboard shortcuts.  I guess there is a quicker way to see all shortcuts used by compz-fusion,  but I am not sure of it.

Good luck,

-Ash R

---

### Post by zeug on 2009-05-29
Could this still have caused the problem if the Windows keys behaves this way even if I run Openbox as the desktop environment (i.e. when compiz is not running?) ?

EDIT I have tried what you said but there are no bindings for the Windows key alone (only with only with combinations of other keys).  However, when I try to make a new binding with Compiz, it seems to recognize the Windows key (as the Super key, as it should) WITHOUT and WITH the Fn-key.
Why is that? O.o

zeug.

---

### Post by zeug on 2009-06-07
Bump.
I need to make the keycode 125 (the FN and Windows keys together) to be replaced with the keycode 126 (just the Windows key).  Compiz does recognize both as the Windows key but none of the shortcuts with the Windows key (125) unless FN and Windows keys are pressed (126).

zeug.

---

### Post by switch10 on 2009-06-07
I'm having the exact same problem.  Does anyone know what is going on here?

---

### Post by switch10 on 2009-06-07
Hey I fixed it (sort of).  check out this thread.  [http://ubuntuforums.org/showthread.php?t=1156339&highlight=super+key+stopped+working&page=2](http://ubuntuforums.org/showthread.php?t=1156339&highlight=super+key+stopped+working&page=2)

you just have to mess around with the keyboard short cuts.  For me as soon as I press the WIN key to assign a new short cut it says that super+L is already assigned to open my browser.  It still wont let me do a key combo i.e. Super+T to open a terminal, but at least the key is recognized now (by itself).  

p.s. if it says MOD4 instead of super, the short cut wont work.

Dave

---

### Post by zeug on 2009-06-08
I went into the Keyboard Shortcut Manager in GNOME and it seems that the shortcuts I made in Compiz are have Mod4 in the shortcuts instead of Super.  Also, it recognizes the Windows key as Super L and the FN key + Windows key as Super R.  This being said it seems that now, after having open GNOME Shortcut Manager, the shortcuts work.  However, how do I make shortcuts as the Mod4 key? I do not know where it is.

Thanks,
zeug.

---

### Post by zeug on 2009-06-08
Okay, I have seemed to fix it.  Change the layout so that is knows it mapped the Windows keys as Hyper keys.

zeug.

---

