---
title: "Window instability in XFCE 4.10: erratic unprompted window switching/transparency"
date: 2015-01-25
forum: Desktop Environments
---

### Post by Eric_Darsow on 2015-01-25
At seemingly random times, my active window will be replaced by the entire screen view of some other seemingly random window open in a different workspace (or another window in the same workspace). Once this other window flashes up and I move my cursor around the screen, parts of the active window I am intending to work on (icons, lines of text, menu bars) will "bleed through" in some places and then disappear as I keep moving the cursor. 

For example, I'll be working in say file explorer just clicking away and all of a sudden a libre office spreadsheet (in a different workspace) will appear instead. As I move my cursor around the screen, individual lines of the file explorer will appear where it would be located if it were the active window. As I move the cursor away, those lines will disappear. My clicking and keyboard still affect my intended active window, it's just that it's covered up by the random flashed window--meaning I'm unable to do anything. The crazy part is even if I close the "offending" window that seems to jump on top of any other application, an image of that window still flashes after its closure until a restart.

I can get back to my intended active window by using hotkeys and it may stay stable for say a minute or 10. I used to think this was an instability created by libre office calc since it seemd I'd only get this problem when i was using a spreadsheet. But now it happens even when a spreadsheet isn't open. the instability usually gets so bad that i have to restart to keep the screen stable.

I'm running xubuntu 14.04 LTS with xfce 4.10 installed as part of the package. I'm running this on a Thinkpad T410 with 8 gig ram. This is a bewildering problem that has been growing worse by day. I have been looking for patterns of when this happens or with what apps, but I can't find any. 

Here's the current configuration of my video drivers. I'm not sure what to do with this info, though. 
```

 *-display               
       description: VGA compatible controller
       product: GT218M [NVS 3100M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:46 memory:cc000000-ccffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:2000(size=128) memory:cd000000-cd07ffff

```

Being relatively new to Linux and video drivers, etc., I'm wondering if you can help me diagnose and fix this increasingly debilitating problems.

---

### Post by kerry_s on 2015-01-25
that's from compositing, disable it in, i think, "widows tweaks".
that will at least allow you to work to fix the issue.

---

### Post by Eric_Darsow on 2015-02-24
Thanks so much--this has saved my computer!

---

