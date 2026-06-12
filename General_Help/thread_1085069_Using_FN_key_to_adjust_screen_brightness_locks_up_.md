---
title: "Using FN key to adjust screen brightness locks up desktop"
date: 2009-03-02
forum: General Help
---

### Post by DustyMP on 2009-03-02
I have a Dell Inspiron 600m and just installed Ubuntu 8.10 alongside XP a few weeks ago. I have a FN key that can be used in conjunction with the up and down arrow keys to raise or lower the screen's brightness. When I try this however the system stops responding.

I can "select" the three menus from the top taskbar. I cannot open them but moving the mouse cursor over them will cause them to highlight. I cannot interact with any open windows. I cannot activate the force-quit icon I put on the taskbar nor can I open the terminal with Alt+F2. 

I can restart with CTRL+ALT+BACKSPACE but the environment is pretty unstable after that. By that I mean applications take forever to load and performance is sluggish at best.

I would love any input about how to fix this. I recognize it isn't a big deal, just more of a convenience issue. I figured it would be a cool opportunity to learn a little more about this OS and this support forum in case I have real problems later.  Thanks.

---

### Post by Rallg on 2009-03-02
I don't know about your particular model. But I have a different Dell, and a few weeks ago, for my system there was a BIOS update that changed the way the brightness works in Ubuntu (it is an improvement).

So, start by going to the Dell support site, and looking for a BIOS update. Since you also have Windows, it is best to update a BIOS that way.

---

### Post by DustyMP on 2009-03-02
Thanks for the heads up. I will try it this evening and post what if any effect that has.

---

### Post by DustyMP on 2009-03-02
OK, so I flashed the BIOS with the latest update to no avail. The system continues to freeze. Any other suggestions?

---

### Post by Rallg on 2009-03-03
Best I can do is guess... When 8.04 was in pre-release, some computers had this problem: One or two of the system "preferences" functions would hang. The process would load into memory, but do nothing. Then, similar processes would hang, in cascade. Whatever caused it was fixed before the 8.04 release, and I haven't seen it in 8.10 on either of my computers.

The cure, when the problem was still there, was to force un-hang the system, then either kill the offending process in System Monitor, or simply launch a "known good" preferences panel, which magically killed whatever was in its way. I don't recall the details.

It sounds as if the brightness application is the problem in your system. Whether it doesn't play nice with the keys, or with the BIOS, might be solved by trying to adjust the brightness in a different way. Can you install a move-the-slider brightness adjustment in the system tray?

Incidentally, on both of my Dell computers (not your model), brightness is adjusted not by Fn with the up or down arrow, but by Fn with other keys (9 for up, 0 for down, on the one I am using now).

There is a last resort that ought to work, if anything at all works on your system: It is possible to make brightness go up or down via shell script. I did this once but do not recall the script (it is not difficult). You could either type the necessary command into Terminal, or have a few pre-made scripts for different brightness levels, that could be picked from your menu.

---

### Post by DustyMP on 2009-03-04
I found the brightness application for the system tray and added it. Works like a charm. Thank you for your help. As many different places as I use the laptop in I really need that.

---

