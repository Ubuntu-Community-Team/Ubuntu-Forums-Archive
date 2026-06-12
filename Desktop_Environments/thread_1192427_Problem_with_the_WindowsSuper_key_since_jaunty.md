---
title: "Problem with the Windows/Super key since jaunty"
date: 2009-06-20
forum: Desktop Environments
---

### Post by toneman77 on 2009-06-20
Hello everybody
After doing a fresh install of Jaunty I couldn't use the win key as a modifier. So I changed the behavior of it in the keyboard settings to "Super is mapped to Win keys" this helped for assigning shortcuts in the keybinding properties.
Since i prefer to use openbox I soon realized that the win key behaved different. All my (openbox) keybindings with the left win key dont work anymore. They do with the right one. They used to work with both.

So I launched xev and got:

Pressing the right win key:
```
KeyPress event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18146912, (541,-354), root:(542,577),
    state 0x10, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18146968, (541,-354), root:(542,577),
    state 0x50, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
Pressing the left win key:
```
KeymapNotify event, serial 82, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 82, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 82, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor
```


Pressing the left win key with left alt:
```
KeyPress event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18242112, (106,-12), root:(107,919),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18242416, (106,-12), root:(107,919),
    state 0x18, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18242576, (106,-12), root:(107,919),
    state 0x58, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18242936, (106,-12), root:(107,919),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

EnterNotify event, serial 82, synthetic NO, window 0x3800001,
    root 0x13f, subw 0x0, time 18243449, (121,21), root:(122,952),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

```

Funny thing is, when i kill gnome-settings-manager, all keys work as expected.
Seems like my left win key acts defferently.

Anyone got an idea?

---

### Post by Alex8080 on 2009-06-23
Hello,

I wanna lay down my experience with the Windows-key a little bit before I answer this thread, since I want to finally make somehow a final thread for this "disease" of not working windows-keys.

1.) The Windows-key per se is just a key like every other key. It is called "Super" and DOES NOT WORK like Alt or Ctrl. You have to explicitly tell Ubuntu that you want to use this Super-key like Alt or Ctrl. Go to Pref -> Keyboard Shortcuts -> Layout / Layout Options and check "Super is mapped to Winkeys".

2.) After that, you can use the super-key in conjunction with any other key and form items like "Mod4+E" or "Mod4+R" for starting up the Explorer or Terminal of your choice. For now, you can JUST define that in Pref -> Keyboard Shortcuts.

What is still missing is:
3.) Since compiz overrules these settings, you should definitly install the package "compizconfig-settings-manager", which gives you a new entry at Pref -> CompizConfig Settings Manager. Open it after install and play a bit around with the keyboard shortcuts and features. I dont know what exactly finally did let me trigger my shortcuts, but after installing ccms, and playing with it, the shortcuts finally do work.

How does it work:
As already described in other threads, you have to press Super and hold it. Then press the other key (for example "E" for explorer) and release E again. But dont let go of the super key the whole time! Thats the trick. You will figure it out after some time.

Hope that helps and give some useful Windows-key-Thread a sticky vote or FAQ-note, cause this would have saved me some time :popcorn:

---

### Post by VCoolio on 2009-06-24
thank you, this clears some stuff up. But at 1) you should point to preferences > Keyboard, not Keyboard Shortcuts. Is obvious if you used these menus before, but for the new users' sakes I thought I'd mention it.

---

### Post by KarenAK on 2009-06-24
I tried it. Didn't work. So far. I'll fiddle with it some more on the weekend.

Thank you for your help :-)

---

