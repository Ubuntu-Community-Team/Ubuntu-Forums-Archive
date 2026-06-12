---
title: "Drag Cursor Garbled in Dapper"
date: 2007-09-21
forum: Desktop Environments
---

### Post by Iowa Dave on 2007-09-21
My Dapper installation has been running great for months. It's been my main production platform for both business and leisure since I assembled this computer. 

But suddenly the mouse cursor changes to a grabled square of random bits during click-and-drag operation. I think it may have started doing this after a recent "Software Update" of XORG components. Or perhaps after a recent kernel upgrade?

My video card (onboard) is VIA Chrome 9. I installed the VIA OpenChrome drivers when I set up the system initially, thanks to great help here on the Forums.  Here's the DEVICE section of /etc/X11/xorg.conf:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

I have searched the Forums. There are some articles about this happening on second screens using ATI video cards. I have not found anything about it concerning VIA hardware or Dapper. I'm feeling stumped at this point.

It is probably a settings issue. Maybe something got changed or reset to a default by the XORG update script. Or else I need to uninstall the last XORG update and revert to the previous format which did work. Or perhaps I need to reinstall the VIA drivers? I read a forum on NVIDIA drivers that states you have to reinstall video drivers after a kernel upgrade. Is that really true?

Before I start blasting away at XORG and my drivers, I would appreciate some words of wisdom from the Forum.

I'm looking for a solution that doesn't involve changing to Feisty, because I want to learn what is going on. Besides, Dapper promised three year-support. I'm taking Ubuntu at its word on that.

Any suggestions for how to resolve this issue in Dapper would be greatly appreciated.

Iowa Dave

---

### Post by Lord Illidan on 2007-09-23
Try re-installing the drivers. Since you've updated the kernel, and the drivers weren't part of it, that is where it might have gone wrong.

---

### Post by Iowa Dave on 2007-09-23
No harm trying that. Will report back on results both here and in the other thread.

---

### Post by Iowa Dave on 2007-09-23
No joy. Followed directions [[COLOR="RoyalBlue"]_here_[/COLOR]]("https://help.ubuntu.com/community/OpenChrome") but the cursor still turns into a flickering square during click-and-drag.

It takes some of the fun out of using Ubuntu. Strange thing is, it didn't do this for many months. So I don't think it is meant to be this way. I suspect that some software update had an unanticipated consequence for the cursor. It beats me, though.:confused:

---

### Post by Lord Illidan on 2007-09-23
Did you try this, also : 

[LIST]
[*] **My mouse cursor sometimes disappears**
 This is known to happen on VN800 and VM800 chipsets. As a solution, you can try to add  
         Option          "SWCursor" "true"
To the device section in your xorg.conf. 
[/LIST]These hardware devices are not known for their linux compatibility..

---

