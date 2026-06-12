---
title: "Delete Key Unresponsive in 10.04 LTS"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Paco009 on 2012-02-17
I recently did a re-install of Ubuntu on my machine and have since been having problems with my delete key. If I select something in nautilus and press delete, the nautilus window maximizes vertically, and nothing is deleted. If I select something and press delete again the window does nothing until it is non-vertically maximized at which point it just re-maximizes.

I thought this might have been an unintended key binding in compiz or something like that, but I have yet to find anything and am fairly confident I didn't change anything involving my delete button.

Additionally, I tried the fix suggested [_**here**_]("http://alexsleat.co.uk/2011/06/11/gnome-3-delete-key-not-deletingworking-in-nautilus/") for a similar problem (changing configuration file settings for desktop>gnome>interface), and although the changes appear to have stuck, nothing about my delete key's behavior has changed.

Any help would be awesome,
Cheers

---

### Post by Copper Bezel on 2012-02-17
It sounds as if the key is being mis-recognized somehow (though I can't imagine as what) due to some accidental modification of the keyboard map. I'm assuming that Delete has the same behavior in other applications? (If not, and it's Nautilus-specific, I wouldn't really know where to start.) But then, if pressing Delete to set the accelerator keybinding worked ... bleh. Let's just be sure.

One easy way to see if it's a Compiz setting is to run metacity --replace from the run dialogue, so Compiz isn't running at all (warning: make sure you have a terminal window running, since killing Compiz will make the Unity interface disappear.) Then, try using Delete in Nautilus and see what happens.

Check the output from pressing the key itself by running xev from a terminal and pressing the key. (I don't remember if xev works without installing a utility package, but it'll let you know, of course.) You should see something like this:

```
KeyPress event, serial 29, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 96790187, (955,361), root:(957,620),
    state 0x0, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XmbLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 96790268, (955,361), root:(957,620),
    state 0x0, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False
```

---

### Post by Paco009 on 2012-02-18
Thanks for the quick response;

After pressing the delete key in several different apps it's apparent that it's a global issue and definitely not nautilus specific. 

I'm hesitant to run metacity --replace simply because I've run into problems switching back and forth between the two in the past with my compiz configuration (one of the reasons I just did the 10.04 re-install). If I can avoid it I'd like to.

I did however run xev and got the following output for my delete key:

```
FocusOut event, serial 36, synthetic NO, window 0x4000001,
    mode NotifyGrab, detail NotifyAncestor

PropertyNotify event, serial 36, synthetic NO, window 0x4000001,
    atom 0x157 (_NET_WM_STATE), time 51573837, state PropertyNewValue

ConfigureNotify event, serial 36, synthetic NO, window 0x4000001,
    event 0x4000001, window 0x4000001, (4,25), width 178, height 767,
    border_width 2, above 0x2aa8b34, override NO

Expose event, serial 36, synthetic NO, window 0x4000001,
    (0,0), width 178, height 10, count 3

Expose event, serial 36, synthetic NO, window 0x4000001,
    (0,10), width 10, height 58, count 2

Expose event, serial 36, synthetic NO, window 0x4000001,
    (68,10), width 110, height 58, count 1

Expose event, serial 36, synthetic NO, window 0x4000001,
    (0,68), width 178, height 699, count 0

PropertyNotify event, serial 36, synthetic NO, window 0x4000001,
    atom 0x1fd (_COMPIZ_WINDOW_DECOR), time 51573851, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4000001,
    atom 0x202 (_COMPIZ_WM_WINDOW_BLUR_DECOR), time 51573852, state PropertyNewValue

FocusIn event, serial 36, synthetic NO, window 0x4000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  68  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

That leads me to believe it is something weird in compiz, but still not sure what. I should also note that when I pressed the key in xev, the window it was running in vertically maximized just like all the others have.

---

### Post by Paco009 on 2012-02-18
After exploring compiz config I found Delete set as a binding under general options to vertically maximize. Not sure how that happened but easy fix lol

Thanks for the help though

---

### Post by Copper Bezel on 2012-02-18
Yep, cool - I'm just glad you found a solution! = )

---

