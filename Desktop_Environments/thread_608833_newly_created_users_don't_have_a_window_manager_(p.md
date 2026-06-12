---
title: "newly created users don't have a window manager (possible caused by upgrade to gusty)"
date: 2007-11-10
forum: Desktop Environments
---

### Post by aefaradien on 2007-11-10
i had a pc with an almost clean install of feisty.  i upgraded it to gusty using the gui update manager with no problems, log back in as first user (the admin one).  everything works fine.

i noticed that some compiz stuff has been installed so i "apt-get autoremove" all packages with "compiz" in the name.  it have given me nothing but trouble in the past and i don't want it.

now when i create a new user (via the gui) and then try to login as that user, gnome starts but there is no window manager.  alt-f2 does nothing but i can still get a terminal from the menu.  here i can type "metacity" and bingo i have a  working window manager.  its all ok so long as i don't close the terminal that started metacity.  if i log of and log back in again, i am back to square 1.

i don't know if the compix thing has anything to do with it at all, just thought i would mention it for completeness.

can someone please tell me where the file that store the setting for the default window manager is?  i have been searching for ages but all the results are spammed up with results to getting compiz working, not removing it.

thanks in advance!

---

### Post by Happy_Man on 2007-11-10
Hehehe.... if it's doing that, then that means that Compiz was working before you removed it. :p 

In any case, go to System --> Preferences --> Appearance, and go to the Effects tab and select "None". If that doesn't restore Metacity, press alt-f2, and enter ```
metacity --replace
``` Either way, from now on, Metacity should start when you log in.

---

