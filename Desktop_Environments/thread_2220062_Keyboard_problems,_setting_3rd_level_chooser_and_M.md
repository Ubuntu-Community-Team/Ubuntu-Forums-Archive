---
title: "Keyboard problems, setting 3rd level chooser and Meta key in Unity"
date: 2014-04-26
forum: Desktop Environments
---

### Post by tom4everitt on 2014-04-26
Hi all,

I've just installed 14.04, and had some problem setting up my keyboard correctly. 

I'm using a Swedish keyboard (MacBook computer), and I like being able to switch between Swedish and English layout for it. This was no problem setting up. 

However:
- I would like to remap the right super key (keycode 134) to work as Alt Gr (aka third level chooser, or ISO_Level_3). In previous versions of Ubuntu that I've used there's been an option for this in the settings, but this option seems to have been pruned. Where can I find it, or is there another fix?
- I would also like to map another key (keycode 104) to become a Meta_L key. 

I made some progress with xmodmap, but then I realized that every time I switched keyboard layout the xmodmap-settings were forgotten. 

Any suggestions would be most welcome.

Thanks,
Tom

---

### Post by tom4everitt on 2014-05-01
Hi again,

I realized that this would probably be best achieved by modifying the xkb-layouts in /usr/share/X11/xkb. I did the following:

1. 
The file /usr/share/X11/xkb/keycodes/evdev controls the key names, i.e. which key the system perceives as what. Here I did:
Set keycode 104 to <AA06> and keycode 134 to <RALT> instead of <RWIN> (also switched above RWIN to RALT, not sure it matters).
Rationale: Changing the name of key 104 will remove it's current behaviour, and changing 134 to RALT automatically changes it's behaviour to Alt Gr (as I wanted).

2. 
The file /usr/share/X11/xkb/symbols/us controls the US-english keymap. Here I added in the "basic" section:
key <AA06> {    [ meta,         meta    ]    };
Rationale: This sets keycode 104 to meta in the US keymap.

3. 
The file /usr/share/X11/xkb/symbols/se controls the Swedish keymap. I similarly added 
key <AA06> {    [ meta,         meta    ]    };
setting keycode 104 to meta in the Swedish keymap.

4. 
Finally run 
dpkg-reconfigure xkb-data
and log out/log in to make the changes take effect. 


This works reasonably well, but with one remaining problem: The meta-key works upon sign-in, but breaks when I switched keyboard layout. Not sure why.

Cheers
Tom

---

