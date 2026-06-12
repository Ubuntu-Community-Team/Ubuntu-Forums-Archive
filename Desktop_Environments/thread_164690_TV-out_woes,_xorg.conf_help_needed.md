---
title: "TV-out woes, xorg.conf help needed"
date: 2006-04-23
forum: Desktop Environments
---

### Post by Mastus on 2006-04-23
So my TV-out won't work. I'm using ATI Radeon 9550SE and I have installed fglrx-drivers and ATI control center. 

I did try to generate xorg.conf with fglrx-config but no luck... I did add the line "ForceMonitors" "CRT, TV" manually (Otherwise the TV won't be recognized, possibly a impedance mismatch on the cables...)

Hardware is working (TV-out does work in Windows).

When I go to ATI Control Center -> TV Out tab, all I got is an "half-sized" desktop on my monitor, and nothing on my TV. 

I think there is something wrong with my xorg.conf, but I can't be certain of that. Is there supposed to be some setup info for TV set? 

Should I always restart X server when enabling / disabling TV-out?

[ATTACH]8667[/ATTACH]

[ATTACH]8668[/ATTACH]

---

### Post by Mastus on 2006-04-23
Got it working.

When Control Panel says to restart X, don't press Ctrl+Alt+Backspace, but logout...



EDIT: Argh, it kind of works. I can see the picture in TV, but only a portion of it. I've tried to search the forums, and haven't found an answer (OK, I am a n00b :( )  how to edit xorg.conf to have a different resolution on TV-out than on monitor.

Is it even possible?

---

