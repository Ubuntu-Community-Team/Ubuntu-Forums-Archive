---
title: "Neverwinter Nights Multiple Accounts and Keyboard Weirdness"
date: 2014-05-29
forum: Gaming &amp; Leisure
---

### Post by kgibson2 on 2014-05-29
After the upgrade to 14.04, some issues have started for my friend when running the Neverwinter Nights client.  The graphics card used is an nvidia 7900 with a single monitor.  There are two accounts and they are multi-boxed (two instances on the same machine).  The problem can appear when one or both accounts are used.  It "appears" related to moving in and out of fullscreen mode with the game. 

The typical scenario is when switching from one account to the other, keyboard activity become erratic.  Sometimes a key will repeat forever, keys may switch their order,  and/or one character may not come till much later in the entry, and characters can be completely dropped.  When not in the chat entry box, of course randomness occurs everywhere from the character running across the screen to windows popping up all over the place.

for example:

"Your mother told you to eat your vegetables"
"Your other mtold you to et your egevtablesssssssssssssssssssssssssssssssssssssss..."


This experience is not duplicated in other applications.  This setup was working fine in the 12.04LTS release.  This is a new experience post-update.  Swapping to a different keyboard has no effect.

Additional Information: 
Graphics card: nvidia 7900
driver nvidia-173
running in gnome-classic

Thanks for any input

---

### Post by kgibson2 on 2014-07-09
This problem is still persisting.  I thought I would share a bit more information about it:

The nvidia driver does not affect the problem.
It does not help to switch from gnome to kde, gnome-metacity, gnome-*.
NWN is being run as native client.

Another player is experiencing the same problem using Ubuntu 14.04 through Wine.  He does not use multiple accounts.  I believe he has an intel video card (4000 maybe?).

The problem appears to be related somehow to fullscreen mode.
closing the application and restarting appears to solve the issue temporarily.

Still looking for answers on this.  Is there a different "backend" we can try.  Our only alternative seems to roll back to the 12.04 LTS version of ubuntu he was using before.

Cheers

---

