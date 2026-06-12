---
title: "Going from GDM to Gnome changes screen mode"
date: 2007-12-29
forum: Desktop Environments
---

### Post by kest on 2007-12-29
Hi there.

I installed a new Ubuntu for my sister -- the old one was years old and had had its repos disabled. I got by with the alternate install CD, installed X and Gnome just fine, but there's a little something wrong with the screen modes.

The default screen mode for 1024x768 is a bit big, extending slightly beyond the physical screen limits; tweaking the monitor itself isn't really an option as this is a dual-boot system and the screen would again get screwy in Windows. I tried to use a modeline from the previous installation, but X didn't use it at all. I renamed it from "1024x768" to "1024x768@85" (which, I google, had helped some people with mode problems) and that was a partial solution: now the screen looks as it should in the GDM login, but when Gnome starts, X seems to change the screen mode to the slightly-too-big default, and gets some ugly-looking black bars in the top-left corner to boot. Without the renaming, GDM starts in the default mode too and there's no change on login.

Here are the relevant parts of the current xorg.conf:
```
Section "Device"
        Identifier      "ATI"
        Driver          "ati"
        BusID           "PCI:0:8:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        ModeLine "1024x768@85"     94.50   1024 1080 1176 1388    768  769  772  808 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes   "1024x768@85" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

In Gnome I haven't found any more fine-grained control for screen modes than setting the resolution and refresh rate, which are the same in the two modes anyway. I don't even know if Gnome is at fault, or if it's GDM-related. I sure didn't find anything strange in GDM's configuration files regarding launching X. Couldn't really find anything interesting in the X logs, either. Anything closely resembling this problem seemed to concern screen resolution instead of the actual modeline being used. I'd be very grateful for even a nudge in the right direction.

---

### Post by adam.tropics on 2007-12-29
Not really sure, but could the repetition in your modes/Screen section be causing any problem?

---

### Post by TeaSwigger on 2007-12-30
Hello, you might try specifying the "virtual display" size; that cured a similar sounding problem for me. 

To do this, first backup your /etc/X11/xorg.conf file. Then open /etc/X11/xorg.conf in an editor with admin privs. Find the Display subsection (with same Depth as the DefaultDepth line). Add a line in that subsection:

```
Virtual 1024 768
```

where 1024x768 is the desired screen size, change accordingly. Hope that helps.

---

### Post by kest on 2007-12-30
**Adam**: I don't really know what you mean by "repetition"; all the mode labels are different, right? To be doubly sure, I took out all the other modes on the Modes line of the Display section, leaving only "1024x768@85", which did nothing to change the situation. The mode still changes on entering Gnome, and I'm still scratching my head.

**TeaSwigger**: I'd seen that come up too, with people who (unlike me) had had their resolution change on them. I gave the Virtual line a try anyway, to no avail.

Thank you for your replies.

---

### Post by kest on 2007-12-31
I think I found the solution. When the Gnome settings say the resolution is set to 1024x768 and the refresh rate to 85 Hz, screen modes with deviating refresh rates aren't accepted. The modeline I prepared in xvidtune had a vsync of about 84.3 to 84.6, depending on the tweaks, and that didn't work; however, when I had gtf produce me a modeline with a vsync of exactly 85, Gnome had no problem using it. While the new modeline (even with slight horizontal adjustment) doesn't look quite as good as the custom one, and while I'd *really* appreciate Gnome not butting in like this, I suppose this is a satisfactory result.

Still, if anyone knows how to make Gnome less strict on the refresh rates, I'd like to know.

---

