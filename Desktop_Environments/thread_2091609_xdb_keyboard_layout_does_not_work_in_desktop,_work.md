---
title: "xdb keyboard layout does not work in desktop, works in tty - please help!"
date: 2012-12-05
forum: Desktop Environments
---

### Post by cheater00 on 2012-12-05
Hi guys,
I have recently tried updating a layout I have, called us_split. In its basic form it's like the us qwerty layout with a small mod. This is to make a specific keyboard (Logitech k400) more usable. The idea is to make the up arrow into right shift, down and right arrows into right ctrl, right control into right alt, and left arrow into left meta. It makes much more sense when you see the keyboard:

[http://i.imgur.com/jkfQY.jpg](http://i.imgur.com/jkfQY.jpg)

I call the new fork us_split_k400. It can be found at:

[https://bitbucket.org/cheater/us_split_logitech_k400](https://bitbucket.org/cheater/us_split_logitech_k400)

the original can be found at:

[https://bitbucket.org/cheater/us_split](https://bitbucket.org/cheater/us_split)

the specific diff can be found at:

[https://bitbucket.org/cheater/us_split_logitech_k400/commits/5f777c7dfe1a4b176b3409c71030ad8f](https://bitbucket.org/cheater/us_split_logitech_k400/commits/5f777c7dfe1a4b176b3409c71030ad8f)

I have found the following issues:

1. Even without the changes above, my layout has regressed. In specific: us_split hard-wires caps to esc. That is, if you press the button to the left of A, you get esc. This isn't recognized anymore. I believe on this pc I have first installed the layout while running a fairly early beta of ubuntu 12.04. I have just reinstalled it (using python install.py) and the esc key to the left of A is simply gone. On the other hand, mapping compose onto the original esc key to the left of F1 works as it did before.

2. in us_split_k400, the arrows and right control don't bear remapping. In specific, only setting the right arrow to control_r worked. The rest didn't do anything. However, the layout worked correctly in a tty after I did sudo loadkeys us_split_k400.

3. The caps-as-esc key developed VERY weird behaviour: it was esc AND caps at the same time. So if you pressed it, you got esc, but the status of caps lock changed as well. Again, this worked under teletype.

I would appreciate any and all tips. This is driving me nuts, and I think it might be representative of a deeper problem. I have no idea where to start, but if anyone would like me to perform any tests I'd love to help out. :KS

  I have tried this under MATE and under Gnome 3 Fallback. They both
have the aforementioned issues.

I am under Ubuntu 12.04, if there are any other questions I'll be
happy to provide the answers.

ThanksP.S. I also posted this on the xorg mailing list: [http://lists.x.org/archives/xorg/2012-December/055142.html](http://lists.x.org/archives/xorg/2012-December/055142.html)

and tried asking in the #mate channel

and of course searched google high and low. :confused:

---

### Post by cheater00 on 2012-12-05
By the way, here's the related section of dumpkeys:

```

keycode 103 = Up
 alt    keycode 103 = KeyboardSignal
 alt    shiftl    keycode 103 = KeyboardSignal
 alt    shiftr    keycode 103 = KeyboardSignal
 alt    shiftl    shiftr    keycode 103 = KeyboardSignal
 alt    ctrll    keycode 103 = KeyboardSignal
 alt    shiftl    ctrll    keycode 103 = KeyboardSignal
 alt    shiftr    ctrll    keycode 103 = KeyboardSignal
 alt    shiftl    shiftr    ctrll    keycode 103 = KeyboardSignal
keycode 104 = Prior
 shift    keycode 104 = Scroll_Backward
 shift    shiftl    keycode 104 = Scroll_Backward
 shift    shiftr    keycode 104 = Scroll_Backward
 shift    shiftl    shiftr    keycode 104 = Scroll_Backward
 shift    ctrll    keycode 104 = Scroll_Backward
 shift    shiftl    ctrll    keycode 104 = Scroll_Backward
 shift    shiftr    ctrll    keycode 104 = Scroll_Backward
 shift    shiftl    shiftr    ctrll    keycode 104 = Scroll_Backward
 keycode 105 = Left
 alt    keycode 105 = Decr_Console
 alt    shiftl    keycode 105 = Decr_Console
 alt    shiftr    keycode 105 = Decr_Console
 alt    shiftl    shiftr    keycode 105 = Decr_Console
 alt    ctrll    keycode 105 = Decr_Console
 alt    shiftl    ctrll    keycode 105 = Decr_Console
 alt    shiftr    ctrll    keycode 105 = Decr_Console
 alt    shiftl    shiftr    ctrll    keycode 105 = Decr_Console
 keycode 106 = Right
 alt    keycode 106 = Incr_Console
 alt    shiftl    keycode 106 = Incr_Console
 alt    shiftr    keycode 106 = Incr_Console
 alt    shiftl    shiftr    keycode 106 = Incr_Console
 alt    ctrll    keycode 106 = Incr_Console
 alt    shiftl    ctrll    keycode 106 = Incr_Console
 alt    shiftr    ctrll    keycode 106 = Incr_Console
 alt    shiftl    shiftr    ctrll    keycode 106 = Incr_Console
 keycode 107 = Select
 keycode 108 = Down

```Note that the arrows are still what they were. They're clearly remapped in the layout:

[https://bitbucket.org/cheater/us_split_logitech_k400/commits/5f777c7dfe1a4b176b3409c71030ad8f](https://bitbucket.org/cheater/us_split_logitech_k400/commits/5f777c7dfe1a4b176b3409c71030ad8f) 
On the other hand, the same layout remaps the k key to type h and that shows: 
```


keycode  37 = +h
 shift    keycode  37 = +H
 control    keycode  37 = BackSpace
 shift    control    keycode  37 = BackSpace
 altgr    control    keycode  37 = BackSpace
 shift    altgr    control    keycode  37 = BackSpace
 alt    keycode  37 = Meta_h
 shift    alt    keycode  37 = Meta_H
 altgr    alt    keycode  37 = Meta_h
 shift    altgr    alt    keycode  37 = Meta_h
 control    alt    keycode  37 = Meta_BackSpace
 shift    control    alt    keycode  37 = Meta_BackSpace
 altgr    control    alt    keycode  37 = Meta_BackSpace
 shift    altgr    control    alt    keycode  37 = Meta_BackSpace

```although after this line it starts showing incorrect values. So it seems like this is a deeper bug. Can anyone comment on that? Is there anyone in specific I could contact about the xkb codebase?

The listing continues with some erroneous and some correct values: ```

 shiftl    keycode  37 = +k
 shift    shiftl    keycode  37 = +K
 altgr    shiftl    keycode  37 = +k
 shift    altgr    shiftl    keycode  37 = +k
 control    shiftl    keycode  37 = Control_k
 shift    control    shiftl    keycode  37 = Control_k
 altgr    control    shiftl    keycode  37 = Control_k
 shift    altgr    control    shiftl    keycode  37 = Control_k
 alt    shiftl    keycode  37 = Meta_k
 shift    alt    shiftl    keycode  37 = Meta_K
 altgr    alt    shiftl    keycode  37 = Meta_k
 shift    altgr    alt    shiftl    keycode  37 = Meta_k
 control    alt    shiftl    keycode  37 = Meta_Control_k
 shift    control    alt    shiftl    keycode  37 = Meta_Control_k
 altgr    control    alt    shiftl    keycode  37 = Meta_Control_k
 shift    altgr    control    alt    shiftl    keycode  37 = Meta_Control_k
 shiftr    keycode  37 = +k
 shift    shiftr    keycode  37 = +K
 altgr    shiftr    keycode  37 = +k
 shift    altgr    shiftr    keycode  37 = +k
 control    shiftr    keycode  37 = Control_k
 shift    control    shiftr    keycode  37 = Control_k
 altgr    control    shiftr    keycode  37 = Control_k
 shift    altgr    control    shiftr    keycode  37 = Control_k
 alt    shiftr    keycode  37 = Meta_k
 shift    alt    shiftr    keycode  37 = Meta_K
 altgr    alt    shiftr    keycode  37 = Meta_k
 shift    altgr    alt    shiftr    keycode  37 = Meta_k
 control    alt    shiftr    keycode  37 = Meta_Control_k
 shift    control    alt    shiftr    keycode  37 = Meta_Control_k
 altgr    control    alt    shiftr    keycode  37 = Meta_Control_k
 shift    altgr    control    alt    shiftr    keycode  37 = Meta_Control_k
 shift    shiftl    shiftr    keycode  37 = +H
 control    shiftl    shiftr    keycode  37 = BackSpace
 shift    control    shiftl    shiftr    keycode  37 = BackSpace
 altgr    control    shiftl    shiftr    keycode  37 = BackSpace
 shift    altgr    control    shiftl    shiftr    keycode  37 = BackSpace
 alt    shiftl    shiftr    keycode  37 = Meta_h
 shift    alt    shiftl    shiftr    keycode  37 = Meta_H
 altgr    alt    shiftl    shiftr    keycode  37 = Meta_h
 shift    altgr    alt    shiftl    shiftr    keycode  37 = Meta_h
 control    alt    shiftl    shiftr    keycode  37 = Meta_BackSpace
 shift    control    alt    shiftl    shiftr    keycode  37 = Meta_BackSpace
 altgr    control    alt    shiftl    shiftr    keycode  37 = Meta_BackSpace
 shift    altgr    control    alt    shiftl    shiftr    keycode
 37 = Meta_BackSpace
 ctrll    keycode  37 = +H
 altgr    ctrll    keycode  37 = +H
 shift    altgr    ctrll    keycode  37 = +H
 control    ctrll    keycode  37 = BackSpace
 shift    control    ctrll    keycode  37 = BackSpace
 altgr    control    ctrll    keycode  37 = BackSpace
 shift    altgr    control    ctrll    keycode  37 = BackSpace
 alt    ctrll    keycode  37 = Meta_h
 shift    alt    ctrll    keycode  37 = Meta_H
 altgr    alt    ctrll    keycode  37 = Meta_h
 shift    altgr    alt    ctrll    keycode  37 = Meta_h
 control    alt    ctrll    keycode  37 = Meta_BackSpace
 shift    control    alt    ctrll    keycode  37 = Meta_BackSpace
 altgr    control    alt    ctrll    keycode  37 = Meta_BackSpace
 shift    altgr    control    alt    ctrll    keycode  37 = Meta_BackSpace
 shiftl    ctrll    keycode  37 = +K
 shift    shiftl    ctrll    keycode  37 = +k
 altgr    shiftl    ctrll    keycode  37 = +K
 shift    altgr    shiftl    ctrll    keycode  37 = +K
 control    shiftl    ctrll    keycode  37 = Control_k
 shift    control    shiftl    ctrll    keycode  37 = Control_k
 altgr    control    shiftl    ctrll    keycode  37 = Control_k
 shift    altgr    control    shiftl    ctrll    keycode  37 = Control_k
 alt    shiftl    ctrll    keycode  37 = Meta_k
 shift    alt    shiftl    ctrll    keycode  37 = Meta_K
 altgr    alt    shiftl    ctrll    keycode  37 = Meta_k
 shift    altgr    alt    shiftl    ctrll    keycode  37 = Meta_k
 control    alt    shiftl    ctrll    keycode  37 = Meta_Control_k
 shift    control    alt    shiftl    ctrll    keycode  37 = Meta_Control_k
 altgr    control    alt    shiftl    ctrll    keycode  37 = Meta_Control_k
 shift    altgr    control    alt    shiftl    ctrll    keycode  37 = Meta_Control_k
 shiftr    ctrll    keycode  37 = +K
 shift    shiftr    ctrll    keycode  37 = +k
 altgr    shiftr    ctrll    keycode  37 = +K
 shift    altgr    shiftr    ctrll    keycode  37 = +K
 control    shiftr    ctrll    keycode  37 = Control_k
 shift    control    shiftr    ctrll    keycode  37 = Control_k
 altgr    control    shiftr    ctrll    keycode  37 = Control_k
 shift    altgr    control    shiftr    ctrll    keycode  37 = Control_k
 alt    shiftr    ctrll    keycode  37 = Meta_k
 shift    alt    shiftr    ctrll    keycode  37 = Meta_K
 altgr    alt    shiftr    ctrll    keycode  37 = Meta_k
 shift    altgr    alt    shiftr    ctrll    keycode  37 = Meta_k
 control    alt    shiftr    ctrll    keycode  37 = Meta_Control_k
 shift    control    alt    shiftr    ctrll    keycode  37 = Meta_Control_k
 altgr    control    alt    shiftr    ctrll    keycode  37 = Meta_Control_k
 shift    altgr    control    alt    shiftr    ctrll    keycode  37 = Meta_Control_k
 shiftl    shiftr    ctrll    keycode  37 = +H
 altgr    shiftl    shiftr    ctrll    keycode  37 = +H
 shift    altgr    shiftl    shiftr    ctrll    keycode  37 = +H
 control    shiftl    shiftr    ctrll    keycode  37 = BackSpace
 shift    control    shiftl    shiftr    ctrll    keycode  37 = BackSpace
 altgr    control    shiftl    shiftr    ctrll    keycode  37 = BackSpace
 shift    altgr    control    shiftl    shiftr    ctrll    keycode 37 = BackSpace
 alt    shiftl    shiftr    ctrll    keycode  37 = Meta_h
 shift    alt    shiftl    shiftr    ctrll    keycode  37 = Meta_H
 altgr    alt    shiftl    shiftr    ctrll    keycode  37 = Meta_h
 shift    altgr    alt    shiftl    shiftr    ctrll    keycode  37 = Meta_h
 control    alt    shiftl    shiftr    ctrll    keycode  37 = Meta_BackSpace
 shift    control    alt    shiftl    shiftr    ctrll    keycode 37 = Meta_BackSpace
 altgr    control    alt    shiftl    shiftr    ctrll    keycode 37 = Meta_BackSpace
 shift    altgr    control    alt    shiftl    shiftr    ctrll keycode  37 = Meta_BackSpace 
```

---

### Post by cheater00 on 2012-12-05
I figured it out. Kind of out of desperation, I just googled for "stackoverflow xkb" and started reading everything. I came across two questions, one that mentioned using modifier_map, and another that mentioned using xkbcomp :0.0 to get a dump of the final layout that's loaded. I had to do the following:

1. set the group 1 explicitly, otherwise the keys only got overridden on group 2.

```

    // Make the lower-right corner of the k400/k400r saner.
    key <RCTL> {
        type="TWO_LEVEL",
        symbols[Group1]=[ Alt_R, Meta_R ]
    };
    key <UP>   {
        symbols[Group1]= [         Shift_R ],
        symbols[Group2]= [         Shift_R ]
       };
    key <DOWN> {
        symbols[Group1]= [       Control_R ],
        symbols[Group2]= [           Alt_R ]
    };
    key <RGHT> {
        symbols[Group1]= [       Control_R ],
        symbols[Group2]= [           Alt_R ]
    };

    // Make the left-over left arrow cursor key a meta key.
    // Apparently, if there's only one meta key, you set it to Meta_L.
    key <LEFT> {
        type[Group1]="ONE_LEVEL",
        symbols[Group1]= [        ISO_Level3_Shift ]
    };

```2. use modifier_map

```

    modifier_map Control { <DOWN> };
    modifier_map Control { <RGHT> };
    modifier_map Shift { <UP> };
    modifier_map Mod1 { <RCTL> };
    modifier_map Mod1 { <RALT> };
    modifier_map Mod5 { ISO_Level3_Shift };

```and 3. delete the other layouts that were loaded. Crazily enough, they modified the layout, even if they weren't selected! so no matter what i did, the up arrow's group1 was always set to Up. This is some sort of bug.

Hope this helps someone. I'd mark this as solved, but I'm not sure how. Maybe one of the moderators can do that if they come across this thread.

Thanks!

---

