---
title: "Konqueror funkiness"
date: 2007-05-29
forum: Desktop Environments
---

### Post by Ateo on 2007-05-29
Basic info:

KDE 3.5.7 (from the kubuntu repos) and Beryl 0.2.1, NVIDIA GeForce Go 7400 (nvidia driver), using my cards built in features and not aiglx/xgl.

-----

This rendering issues only seems to occur with Konqueror. It occured with KDE 3.5.6 so I upgraded to 3.5.7 hoping it fixed it. It did not.

Both uses of Konqueror tweak out on occasion and at completely random times. There is no pattern except that it only occurs when I use the 'wheel' feature of my usb mouse OR my touchpad (synaptics). It happens most frequently when I scroll one 'wheel click' at a time, slowly but it does happen when I scroll up and down quickly. The funk that stick is fixed just by clicking the mouse anywhere, or better yet, if there is a user event on the screen.

I have experienced funks when I submit a form and the page refreshes but some of the form is left over. In other words, the previous screen (usually just some of it) is left superimposed over the new page (again, a click removes it).

It's as if the 'screen refresh' of Konq windows glitches and doesn't complete the rendering.

When I open Konq as a file manager, sometimes the icons funk out (again, fixed by clicking somewhere).

Are there any hacks that I should apply to xorg.conf to work better with beryl? I already have a bunch of options so I'm kind of hoping for some advanced stuff here. Are there any options in beryl that I should look into specifically?

I've attached 2 screenshots...

Any advice appreciated.

---

### Post by Ateo on 2007-05-29
I am also finding that this occurs with Kopete too. When I type in a new message, the scrolling stick when it tries to add my message to the top half of my chat window. Same applies when a message is sent to me.

---

### Post by Ateo on 2007-05-30
This has been resolved. The issue was a mixture of my xorg.cong, nvidia-settings and beryl. Setting a modeline in X and setting all to 60Hz seemed to resolve the redraw isssue.

The biggest alteration came to xorg.conf changed :```
Section "Module"
    Load        "i2c"
    Load        "bitmap"
    Load        "ddc"
    Load        "extmod"
    Load        "freetype"
    Load        "glx"
    Load        "int10"
    Load        "vbe"
    Load        "nvidia"
    Load        "synaptics"
    Load        "kbd"
EndSection
```

TO

```
Section "Module"
        Load  "glx"
        Load  "extmod"
        Load  "xtrap"
        Load  "record"
        Load  "dbe"
        Load  "freetype"
        Load  "type1"
        Load  "nvidia"
        Load  "synaptics"
        Load  "kbd"
EndSection
```

---

