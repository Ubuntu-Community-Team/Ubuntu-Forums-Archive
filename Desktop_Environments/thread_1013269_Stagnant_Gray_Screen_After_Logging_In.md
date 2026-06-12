---
title: "Stagnant Gray Screen After Logging In"
date: 2008-12-16
forum: Desktop Environments
---

### Post by rotundrory on 2008-12-16
I have been using Hardy (8.04) for several months now. Normally when I log in, the screen goes gray for 1 or 2 seconds before launching into my normal desktop environment. Now when I log in, however, nothing advances beyond the gray screen.

This all started when Rhythmbox tried to play what I guess was a corrupted mp3, causing Ubuntu to freeze up. When I restarted, I got this unmoving gray screen. (I realize this might be unrelated.)

When I hit Ctrl-Alt-F1, I see that there is some error with GNOME Display Manager (duh), and then I get the following output over and over. 

[Please note the numbers in brackets I've written on the left are in this instance random and are strictly increasing from one line to the next.]

```

[39.58784]   ata1.00: status: {DRDY ERR}
[39.59125]   ata1.00: error: {UNC}
[39.59230]   ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[39.59598]   ata1.00: BMDA stat 0x25
[39.59125]   ata1.00: cmd c8/00:08:4e:e6:2c/00:00:00:00:00/e6 tag 0 dma 4096 in

```

Again, these error messages repeat, and I'm unable to enter any commands.

A single time, I was able to Ctrl-Alt-F7 it, and my desktop picture came up, but I wasn't able to do anything.


I can log in with the "safe terminal" mode and see all my files, et cetera. After an inconsistent amount of time, though, this sometimes freezes up.

Someone help me, because Windows is awful.

HELP!

---

