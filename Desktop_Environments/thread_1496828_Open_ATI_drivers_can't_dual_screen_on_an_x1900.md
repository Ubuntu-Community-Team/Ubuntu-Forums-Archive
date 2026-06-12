---
title: "Open ATI drivers can't dual screen on an x1900"
date: 2010-05-29
forum: Desktop Environments
---

### Post by CvdW on 2010-05-29
I am having a strange issue with my Radeon x1900 video card. I have two displays, they work just fine under Windows XP - however in Lucid the secondary display goes into power saving mode as X kicks in.
Ubuntu is convinced that the secondary display is alive and working and lets me drag into it and and relocate it, the only problem is that the display remains powered off the entire time.
ARandR is also convinced that the monitors connected to DVI-0 and DVI-1 are powered up and functioning.
The one strange thing I have found is that X seems to believe that there is an S-Video connector on this card - there is not, all it has are the two DVI connectors.
I am wondering if there is something strange going on with the probing of the supposed S-Video port that is turning off the secondary DVI. I suspect this becuase the xorg.0.log shows a line that reads "(II) RADEON(0): Output S-video using monitor section Monitor0"
Perhaps someone knows how I can force this non-existent port out of existence ?
I cannot use the latest ATI drivers that support this card (version 9.3) because ATI haven't supported the current version of X in those drivers - I would also prefer to not to us their proprietary garbage.
Any constructive ideas would be most appreciated - I have tried everything I have found with no solution.
I have attached the files that I think might be necessary (xorg.0.log has been trimmed to fit within the 19k file size limit)

---

### Post by PGHammer on 2010-05-30
> **CvdW said:**
> I am having a strange issue with my Radeon x1900 video card. I have two displays, they work just fine under Windows XP - however in Lucid the secondary display goes into power saving mode as X kicks in.
Ubuntu is convinced that the secondary display is alive and working and lets me drag into it and and relocate it, the only problem is that the display remains powered off the entire time.
ARandR is also convinced that the monitors connected to DVI-0 and DVI-1 are powered up and functioning.
The one strange thing I have found is that X seems to believe that there is an S-Video connector on this card - there is not, all it has are the two DVI connectors.
I am wondering if there is something strange going on with the probing of the supposed S-Video port that is turning off the secondary DVI. I suspect this becuase the xorg.0.log shows a line that reads "(II) RADEON(0): Output S-video using monitor section Monitor0"
Perhaps someone knows how I can force this non-existent port out of existence ?
I cannot use the latest ATI drivers that support this card (version 9.3) because ATI haven't supported the current version of X in those drivers - I would also prefer to not to us their proprietary garbage.
Any constructive ideas would be most appreciated - I have tried everything I have found with no solution.
I have attached the files that I think might be necessary (xorg.0.log has been trimmed to fit within the 19k file size limit)

There are definite issues with all cards that can *force* the issue (proprietary vs. FOSS).  With the X1K series, it has now passed into *legacy* status (even in Windows), so no proprietary driver is current; worse, the X1K series (including your X1900, doubtless the best performer of that series) was poorly documented compared to any of the HD series GPUs that followed it, so the only real open-source alternative is the radeon (not radeonhd) driver.

I recently upgraded my multi-boot PC's GPU from the HD3450 (well-supported by both proprietary and FOSS, but limited by the 256MB of DDR2) to the HD5450 (512MB of GDDR3, well-supported by the proprietary drivers, but UNsupported by FOSS at present).

The issue with portable computers (laptops, notebooks, and netbooks) is even worse, as they have GPUs that can't be upgraded.

You may well have to consider dropping back to Jaunty (the last LTS release) if you have a X1K-powered portable; if you have a *desktop* with such a GPU, upgrading to the better-documented HD2xxx/3xxx/4xxx would at least let you use current FOSS drivers.

---

