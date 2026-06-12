---
title: "Ubuntu Herd  - Feisty i386 Alternate CD - Long test = Pass"
date: 2007-01-18
forum: Development CD/DVD Image Testing
---

### Post by ahaslam on 2007-01-18
Test case type: Ubuntu Feisty X86 - Alternate CD - Long test.
Image ID: [http://cdimage.ubuntu.com/releases/feisty/herd-2/feisty-alternate-i386.iso](http://cdimage.ubuntu.com/releases/feisty/herd-2/feisty-alternate-i386.iso)
Dowloaded and burned: feisty-desktop-i386.iso
Date of testing: 18.jan.2007
Md5sum confirmed: Yes.
Pass/Fail: Pass
----------------------------------------------------------------------------------------

Followed the full test: [https://wiki.ubuntu.com/Testing/Long](https://wiki.ubuntu.com/Testing/Long) - resulting in a pass ;)
Hardware specs (if applicable) can be found here: [http://www.ubuntuforums.org/showpost.php?p=2021641&postcount=1](http://www.ubuntuforums.org/showpost.php?p=2021641&postcount=1)

*There were a few points that I couldn't cover, those being: 3, 5, 17, 20, 21 & 24.*

[U]
A few points worth considering:[/U]

CPU scaling works otb, but is set via GPM, overriding any cpufreq command placed in rc.local. See my experience & recommendation here: [http://www.ubuntuforums.org/showthread.php?t=341029](http://www.ubuntuforums.org/showthread.php?t=341029)

When putting my laptop to sleep it doesn't unmount any attached usb discs. When resuming I get the warning, "unsafe device removal".

When testing the help features in the apps needed to run the test, no help would load in 'user settings'. This didn't affect the result as it isn't specifically 'online'.

When attaching my digital camera I get the pop up window asking whether to import photo's, after accepting nothing happens. Camera import works form F-Spot & it detects my camera perfectly.


I hope this is of some use, bring on the breakage ;)

Tony.

---

### Post by pochu on 2007-01-18
Nice to hear that!

But please, report your issues at Launchpad (first search if they have already been reported), and tell here which are them.

Thanks
Pochu

---

### Post by ahaslam on 2007-01-18
Regards GPM & USB/sleep I didn't know whether it's normal behaviour, can anyone confirm?
I will search Launchpad on the other points.

Tony.

---

