---
title: "TwinView with secondary LeftOf driving me barmy"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Marakai on 2007-10-22
UPDATE: Thought I might post my solution, after a day of hammering away at it. Finally works JUST the way I want it to!

This is the relevant section of the xorg.conf, the Screen settings.

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "UseEdidFreqs" "True"
    Option         "metamodes" "DFP-1: 1920x1200, DFP-0: 1280x1024"
    Option         "UseDisplayDevice" "DFP-1, DFP-0"
    Option         "ConnectedMonitor" "DFP-1, DFP-0"
    Option         "HorizSync"       "DFP-1: 30-83; DFP-0: 30-81"
    Option         "VertRefresh"     "DFP-1: 56-76; DFP-0: 55-76"
    Option         "TwinViewXineramaInfoOrder" "DFP-1, DFP-0"
    Option         "TwinViewOrientation" "DFP-0 LeftOf DFP-1"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

```

Maybe some of these are superfluous, but I'm at the "If it ain't broke don't touch it" stage. \\:D/

Original Post:

> 
OK, I have just about run out of ideas - and a deadline looming. This either works or I'm stuck going back to Windoze. Please don't let it come to this! :oops:

I have a dual screen setup with Gutsy:

Primary is a Dell 2407 (1920x1200), sitting in front of me. Off to the left side is my scratch-pad screen, an IBM L170p (1280x1024).

All I want is for each monitor to run at its prime resolution, with the primary display having all menu bars, and the secondary just a big empty area (I generally run VMWare virtual machines "over there" running some servers, while all the action happens "in front of me" on the big screen).

Just like Windoze allows, with a few clicks and buttons.

I've googled my fingers to stumps, used nvidia-settings (I'm running nvidia-glx-new) and tried to put an xorg.conf together manually, from scratch.

Nothing works the way I want it to.

I get any combination of the things I want but not ALL:

- screens will be at their resolution, but the secondary is the main screen with all the menu bars

or

- screens will be at their resolution, menu bars on my primary, but LeftOf does nothing and the IBM screen acts like it's sitting to the right of my main

or

- secondary screen is correctly at LeftOf, menu bars on Dell (primary), but the bloody resolution will be that of the secondary (IBM) for both screens

To summarise:

Of the 3 things I want (Dell primary@1920x1200/IBM secondary@1280x1024, IBM LeftOf, Dell has menu bars/IBM empty area) I can apparently get 2 out of 3 only.

ARGH! This shouldn't be this hard. Frustratingly I have the a similar setup at work - except for various reasons it's the "classical" primary=leftof/secondary=rightof and that works. I don't "hate" Linux or Ubuntu for it, but nVidia really needs to improve their config tools.

I'd post my xorg.conf, except I wouldn't know which of all the messed up ones I should pick. :(

Help!
Mike


---

### Post by Marakai on 2007-10-23
:roll: Sorry for the posting noobishness, been a long day:

Just wanted to add that this also all work very well with Compiz Fusion and anything else I throw at it. No issues.

Mike

---

