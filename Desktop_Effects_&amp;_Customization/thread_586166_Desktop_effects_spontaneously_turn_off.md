---
title: "Desktop effects spontaneously turn off"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Kensey on 2007-10-22
I just upgraded to 7.10 on my Dell Latitude D610 and I'm loving the new desktop effects.  However, I'm noticing that periodically, my effects will turn off: the screen flickers and then I get the regular GNOME titlebars and all effects are disabled.  I notice two things when it happens:

* a line is written to .xesssion-errors saying "X connection to :0.0 broken (explicit kill or server shutdown)."
* If I go to System -> Preferences -> Appearance and click the Visual Effects tab, the setting is set to None instead of Custom.  If I reset it to Custom everything comes back... until the next time it happens.

I'm using AIGLX (I uninstalled Xgl).  My Custom effect set includes:

Accessibility:

Enhanced Zoom Desktop
Negative

Desktop:

Desktop Cube
Expo
Rotate Cube
Viewport Switcher

Effects:

Animations
Fading Windows
Trailfocus
Window Decoration
Wobbly Windows

(There are others, but I believe they are all the default set)

The problem seems to have started when I turned on Trailfocus, Wobbly Windows, Desktop Cube or Rotate Cube.  Anybody else noticed this issue with one or more of those plugins?  Also, anybody else noticed serious instability in Firefox when using desktop effects?

---

### Post by overdrank on 2007-10-23
Hi and I am assuming that the laptop has a Ati graphics and it could be cause of the amount of memory. You could use the system monitor and check to see when it disables again the amount of memory in use during the issue. Then maybe disable one effect at a time and see if it will have a impact. Good luck!

---

### Post by ic00 on 2007-10-23
I am having the same problem except lost effects after reboot. And also I lost my cube thing too. Working on it...

---------------------------------
Nvidia 6600GT OC

---

### Post by alperyilmaz on 2007-10-23
I'm having the same problem. I have Intel 855 graphics. 
I don't get flicker like Kensey has. Suddenly everything is reset in terms of desktop effects. Number of workspaces is decreased to 2. I hope we can find the solution soon.

---

### Post by Kensey on 2007-10-25
> **overdrank said:**
> Hi and I am assuming that the laptop has a Ati graphics and it could be cause of the amount of memory.

I thought of memory just now too.  It's actually using Intel GMA945 graphics, but I think it has the minimum amount (128 MB) of shared memory allocated to video.  I recently upgraded from 512 to 1024 MB of RAM, perhaps it's time to boost the video memory allocation as well.

---

### Post by Robor on 2007-10-25
Same problem here.  I've got an Nvidia 5200Go in this laptop and desktop effects randomly turn off.  Normally I can do a 'compiz --replace' to re-enable them but now that is failing.  Going to reboot here and see what happens...  :confused: 

Edit:  I guess I should post the error output:

robor007@RBelin-Ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by ic00 on 2007-10-26
After a day, I figured out that it was my Beryl manager causing the effect disappear everytime I reboot. So I completely removed it and only keep Emerald Theme Manager. Since Beryl is dead and no cube for me, I'll try compiz fusion with Emerald. I have seen many ppl here having problems with compiz fusion, but I'm gonna give a try and let you know if it goes well.

---

