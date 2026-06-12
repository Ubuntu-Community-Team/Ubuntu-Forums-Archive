---
title: "Screen resolution drop down list doesn't ."
date: 2006-09-19
forum: Desktop Environments
---

### Post by carlwenrich on 2006-09-19
...so I can't install (bring files down from the cd to the hard drive) because the screen is at 640x480 and the instructions (and some of the buttons) fall off the screen. Any ideas?

---

### Post by Wolki on 2006-09-20
> **carlwenrich said:**
> ...so I can't install (bring files down from the cd to the hard drive) because the screen is at 640x480 and the instructions (and some of the buttons) fall off the screen. Any ideas?

Just to make sure I understand your problem correctly:

You have the Ubuntu Desktop CD and want to install it to your hard drive. Your screen resolution isn't detected correctly, however, so you are stuck at 640x480 and can't install the Operating system. Is this correct?

The problem is that your monitor does not tell Ubuntu what resolution and refresh rates it can do, so it will assume that it can only do 640x480 to not damage your hardware. Due to technical restricitons this has to be done before the graphical environment starts. This is not that difficult in most cases once you have an installed system (for help, see [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)  - often the first step should be enough, the others are mostly for special cases), but is a bit inconvenient for livecds.

Here's what you could do:
1) Download the alternate install cd from the ubuntu servers - their installation is via a text-mode nearly-graphical interface, it's not harder than the Desktop CD for installation, but will sometimes work where the other doesn't and will work on all resolutions.
2) If you don't want to do that, you can install with the Desktop CD. The trick is that you can move windows by holding "alt", then dragging the window anywhere with the left mouse button. This should allow you reach all the buttons and read all the text.
3) You can try to follow the steps in the help document I linked above on the Desktop CD.

---

### Post by AlbertTatlocksCap on 2006-09-20
I had the same problem when first installing on one of my PCs.

I managed to use the TAB key (by experimenting)to get to the correct button and then the ENTER key to move to the next screen.

Once the install was complete then I reconfigured the xserver to get the correct driver installed. It is a bit of trial and error but there are only a few screens to navigate thro'

---

