---
title: "kubuntu 9.04 very slow, possibly ati drivers. Need some help with some settings"
date: 2009-04-25
forum: General Help
---

### Post by tweaked_influx on 2009-04-25
Hello. I just did a clean install of Kubuntu Jaunty today. I was previously using ubuntu intrepid, had no problems and ran smoother than ever. I like the look of KDE 4.2. The first boot took a while, and things generally responded slowly, so I played around a bit then rebooted. Second boot was faster, however everything still responds slowly. Example, moving a window for the fisr time the mouse cursor will move, but the window will take about 3 seconds before it moves. I have to resort to using the traditional file explorer style desktop rather than using the plasmoids. I tried with the plasmoids, and just trying to move one across the screen the whole system froze I had to do a hard reboot. 
I read through some of the bugs and noticed a few people reporting problems similar to what I'm having with the open source ati driver. It said a possible fix is to switch EXA to XAA. Forgive my ignorance but I have no clue what this means, or how to even do that. Also it mentioned (the bug reports) to make sure my virtual size isn't set too high, again what is this?
My specs are:
IBM Thinkpad R50, Intel Pentium M 1.5Ghz, 732MBram, ATI Mobility Radeon 7500 32MB. 
I know my graphics card isn't the greatest, I don't need too many desktop effects I would just like everything to run smoothly. I had no trouble running compiz with this same computer on Ubuntu Intrepid. 
Sorry for the long post. If anybody needs more info, let me know.
Thanks A million!

---

### Post by satandole666 on 2009-04-27
I'm having the same problem with almost the same setup.  P4 1.6ghz, 512mb VRAM, and a Mobility 7500 with 16mb.

This page will show you how to edit your xorg.conf file to change the XAA or EXA accel along with the virtual size:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Some tweaks are down at the bottom as well.  If I get any major results I'll post it up.

---

### Post by tweaked_influx on 2009-04-29
Well, just for the heck of it I dl'ed the CD for ubuntu jaunty and ran the live CD. Everything ran smooth, until I set up my Acer X193W 19" LCD to the thinkpad. Then, I got the same performance as I did in KDE. After about an hour of googling possible problems, I gave up and figured eh, what the heck, and just added "option" "AccelMethod" "XAA" to my xorg-config file, and voiala. A few things still lag a little bit (mainly firefox). And it starts to lag if I have more than three things open on each of my 4 virtual desktops, but other than that it seems XAA gives better performance on older ATI cards. Hopefully there will be an update to the driver soon to tweak the performance back to the way it was in intrepid.

---

