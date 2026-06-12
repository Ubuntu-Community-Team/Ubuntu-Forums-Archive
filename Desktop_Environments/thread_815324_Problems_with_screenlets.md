---
title: "Problems with screenlets"
date: 2008-06-01
forum: Desktop Environments
---

### Post by besby11 on 2008-06-01
Hello, I have the System Monitor screenlet installed. I would like it to launch on login and be locked to the right side of my screen. I got it to start on login but it always forgets my settings. ( to lock and its position) is there any way to fix this?

---

### Post by mutzinet on 2008-06-04
Kind of the same problem here:
I have three screenlets: System monitor, clock and calendar. 
- The system monitor starts at login but forgets its position
- The clock and the calendar never start at login...
This is quite anoying, so I'm also interested in a fix. ;)

---

### Post by hariprs on 2008-06-04
Same problem for me also

---

### Post by UbuGr on 2008-06-04
I had the same problem, i uninstall screenlets until find a fix for this..

---

### Post by mutzinet on 2008-06-05
Funny thing: When I start KDE instead of gnome, all the screenlets start as they're supposed to...

---

### Post by websurrfr on 2008-08-14
I am having the same problem that my SysMonitor screenlet will not save its settings when I reboot.  I found a few threads on this subject with no solution.  Perhaps someone out there has an idea?

---

### Post by websurrfr on 2008-08-14
Just my luck that I came up with a solution immediately after posting but here it is-


After getting SysMonitor to where you want it, right click on it, select Window, and select Widget.  Now, go to System > Preferences > Advanced Desktop Settings.  Select Widget Layer.  Appearance tab, put background brightness to 100.  Behavior tab uncheck end widget mode on click. Back, and make sure you check the box next to Widget layer.  

When you log in now you just press f9 to toggle your SysMon widget on or off and it will appear in the proper position.

---

### Post by Meharisian on 2010-06-27
I had a similar problem where the screenlets that I set to 'Keep below' would get automatically reset on reboot and would have both 'Keep above' AND 'Keep below' checked, and in effect the 'Keep above' would take over making the screenlets appear above all windows instead of below.

Forums didn't have the solution, but after a bit of tinkering I have a solution that worked for me... perhaps this would be useful for you.

On the mid-bottom left-side of the **Screenlets Manager** window, select **Options** (see attachment)

Change the settings in the **New Screenlets Attributes** window that opens to the settings that you prefer, press ok.

On reboot, your screenlets should be fixed.... **Note**: If this does not work, cancel all 'autostart' settings on screenlets, close all screenlets, then select the settings you want in Options>New Screenlets Attributes and then re-open your screenlets, select 'Autostart on boot' as you wish and it should all be dandy.

Hope that was useful. Enjoy :)


**- Meharisian**

*"Waste no more time arguing what a good man should be, be one." -  Marcus Aurelius*


**My PC Specs:**
Intel i5 750 Quad Core 2.66 GHz
3 GB RAM
1 TB HDD dual boot 45% Windows 7 and 45% Ubuntu 10.04 Lucid 64-bit (rest  10% misc storage + swap)

---

