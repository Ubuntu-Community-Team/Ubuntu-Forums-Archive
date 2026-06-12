---
title: "Bad window redraws in 13.04 with AMD card"
date: 2013-11-08
forum: Desktop Environments
---

### Post by mjpelmear on 2013-11-08
Hello,

I'm running 13.4 on a AMD FirePro 4800 (3 monitors, with Unity desktop). I'm using whatever driver the OS installs by default. (xserver-xorg-video-ati/xserver-xorg-video-radeon?)

I encounter strange redraw issues in a few places:
1) Thunderbird: when selecting multiple messages, will highlight the select messages but also chunks of other messages, sort of, and frequently no longer displays the text over the highlight. It's just a big block of orange.
2) LibreOffice: Sometimes (I'm not sure when exactly) I end up in a situation where the window doesn't redraw unless I move it, and the cell properties dialog in Calc (for example) is just an empty window when it shows up.
3) ghome terminal: sometimes the popup menu will no longer draw the text on top. Rebooting seems to be the only solution I've found here.

These seem to me like they're all related to each other. I'm assuming someone else has encountered this but I haven't been able to find any threads about it anywhere (perhaps because it's so difficult to describe the problem clearly).

Does anyone have any thoughts/suggestions as to what might be causing this? I don't know enough about the "recent" changes in Ubuntu to even know where to start. (I knew X/gnome pretty well.. but it's a brave new world now.)
I gave up on fglrx because it led to the demise of the last build of this machine, but will consider it if that's the only solution.

Thanks,
Matt

---

### Post by mjpelmear on 2013-11-13
Bump.

No one else has encountered this?
100% dialogue windows in LibreOffice are unusable. I was really hoping not to have to start randomly swapping out driver and GUI packages until I find the culprit. :-/

---

