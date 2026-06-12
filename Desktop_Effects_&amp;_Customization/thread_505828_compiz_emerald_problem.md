---
title: "compiz emerald problem"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by skaspud on 2007-07-20
I DLed the emerald package stuff, but when i tried emerald --replace
this happened:
(emerald:11941): Wnck-WARNING **: Unhandled action type (nil)
like 11-12 times
it took forever to get compiz working, but now i'm stuck with this ugly theme, if someone could please help it would be greatly appreciated.
thanks

---

### Post by Mayfairy on 2007-09-16
I tried the guide to update to Gutsy's kernel but iit screwed things up. Undid everything that I did as was told in the guide. 
Then I had to play around with xorg.conf and Nvidia drivers to get X working. Now I even managed to get compiz running. Application switcher and transparency do work and stuff. 
What doesn't work though are Kiba-dock and Screenlets, which only show white blank space where the screenlets and kiba-dock bar are supposed to appear. 
Also Emerald window decorations won't appear and doing 'emerald --replace' gives the same message you have. Only that 11941 is replaced by 5473.


Installed new Nvidia drivers and after that everything works fine again. Emerald still gives that error message but still works correctly.

---

