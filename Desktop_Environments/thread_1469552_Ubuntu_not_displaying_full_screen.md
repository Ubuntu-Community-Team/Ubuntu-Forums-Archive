---
title: "Ubuntu not displaying full screen"
date: 2010-05-02
forum: Desktop Environments
---

### Post by dushy4 on 2010-05-02
Hi,
I am new to ubuntu and was using 9.10 for a while. Now i upgraded to 10.04 and everything was fine untill i install xscreensaver-gl-extra for screensavers. after installing i clicked on screensaver and the whole desktop crashed saying "couldnot detect monoitor etc."

Now the diplay is not fullscreen leaving some space at the bottom(screenshot) . Except cairo dock,nothing is displayed here(see screenshot-1).

I tried sudo dpkg-reconfigure xserver-org but nothing happened.
When i enter compiz in terminal i get "WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!"

I dont want to reinstall ubuntu so please help me to solve this problem.
:(

---

### Post by dushy4 on 2010-05-05
hi,,still waiting for any solution,,,,,
or can anyone tell me which file  or setting is responsible for this so that i can try to fix it myself

---

### Post by robert shearer on 2010-05-05
Have you tried un-installing xscreensaver-gl-extra  ??

---

### Post by denham2010 on 2010-05-05
It actually looks like a second panel has been created somehow....just a thought.....

Have you tried right clicking on the lower bar to see if it is a panel, or just a 'graphics glitch'?

The reason it appears like a panel to me is in the first screenshot, the dock is sitting above the 'bar' (which indicates dock / panel behaviour to me), while in the second image, the dock has managed to position itself at the bottom of the screen (which can happen if both are set to act as a dock / panel).

Cheers.

---

### Post by dushy4 on 2010-05-05
> **denham2010 said:**
> It actually looks like a second panel has been created somehow....just a thought.....

Have you tried right clicking on the lower bar to see if it is a panel, or just a 'graphics glitch'?

The reason it appears like a panel to me is in the first screenshot, the dock is sitting above the 'bar' (which indicates dock / panel behaviour to me), while in the second image, the dock has managed to position itself at the bottom of the screen (which can happen if both are set to act as a dock / panel).

Cheers.


OMG,,,it was an empty panel,,,,just deleted it and it works,,,,,,,simple solution to what seems like a big problem. ,,,, strangely,,i don't notice it all the time.

thanks a lot man,,,,(i am feeling like a stupid right now  :lolflag:)

---

