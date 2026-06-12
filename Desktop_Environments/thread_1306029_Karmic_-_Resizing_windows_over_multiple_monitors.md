---
title: "Karmic - Resizing windows over multiple monitors"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Shootfast on 2009-10-30
Hi Folks,

I've come across a strange "bug" when resizing any window on 9.10 Karmic.
I've got multiple monitors configured with Nvidia TwinView, and when I click and drag a window corner to resize, my resize outline will stop at the monitor divide. 
This behaviour isn't replicated though when using the keyboard shortcut Alt-F8 or Alt-MiddleMouse.

Anyone else get that issue or know of a fix?
I've gone through all the compizconfig settings and obvious menus :/

Cheers

EDIT: This worked fine on jaunty

---

### Post by wetmonkey on 2009-11-01
:bump:  - Same issue, exact reproduction.  I diffed the xorgs before and after and the differences were not to the nvidia portions...   
Still looking at solutions.

---

### Post by TheBuzzSaw on 2009-11-01
I believe you can disable such barriers in the Compiz settings.

---

### Post by wetmonkey on 2009-11-01
It's definitely related to compiz.  If I disable than I can resize across monitors. 

I have been looking around for the setting in compiz.  No luck yet.

---

### Post by TheBuzzSaw on 2009-11-01
Have you installed the compizsettings package yet?

---

### Post by wetmonkey on 2009-11-02
Yes.  Just can't find the actual setting to change.  
I should have copied my settings before upgrading.  Several items were reset during upgrade to 9.10.

---

### Post by TheBuzzSaw on 2009-11-02
I believe it is in the snap-to-edges area. You can uncheck the rules regarding attract/repel.

---

### Post by wetmonkey on 2009-11-02
Couldn't find a setting which worked in that area.  

I am also fighting with key bindings not taking.  Initiate window resize in "Resize Window" and Initiate Window Move in "Move Window" refuse to switch with each other.   

:(

---

### Post by anodos on 2009-11-02
I have this exact same problem - nvidia, twinview, compiz - can't resize any windows past screen boundaries... it's hard and fast, and no settings seem to affect it.  A solution would be nice. :)

---

### Post by wetmonkey on 2009-11-02
Here is the bug I am watching/posting in launchpad
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378")

---

### Post by spodesabode on 2009-11-11
Just to say that I'm having the same issue - Karmic, upgraded from Jaunty - Nvidia 190 drivers.

---

### Post by TheBuzzSaw on 2009-11-11
Curse you all. Now I am having that problem, and I have no idea what I changed. Karmic koala indeed...

---

### Post by Spectre5 on 2009-11-25
Also having this problem...it is very annoying.

---

### Post by jon.mithe on 2009-11-25
ha, I have this problem tried to find a solution by looking on this thread then actually stumbled on a "solution" (I use that loosly..)

The resizing snapping only seems to happen when you try and resize with the frame on your screen and you try to resize across the 2 monitors, or having a frame straddle the two monitors and you try to resize the small side (then it snaps back onto the other monitor)

So the way I found to resize windows was to put the window in the middle of the screen and nudge it so it is just off center, then you are free to expand it all you want on the larger side.

I.e. put a window in the middle so it is 45% on your left monitor and 55% on your right hand monitor.  You can then resize the right hand side all you want.  If you hit the right hand extreme and want it bigger, let go, move back to just off center and repeat.

Not that great, but at least now I can stretch my eclipse 2/3 away my dual monitor setup :)

Jon.

edit: Yeah you can get it 90-95% across both screens quickly, but the amount of space you can increase by per repeat drop by ~0.5 each time (maths is fun.. :/) so there comes a point where to get it all the way across may take forever....

---

### Post by alex2399 on 2009-11-27
There is "half" solution working for me. I have 2 1680x1050 screens.
If you navigate to Compizconfig, there is a general button with a tab display settings in it.
For me it listed 1680x1050+0+0 and 1680x1050+1680+0
I changed it to 3360x1050+0+0 and disabled "Detect outputs".

Now Compiz sees my screens as one big desktop and you can stretch a window on two screens, even going fullscreen in a window makes it go fullscreen over both screens.
There is however a downside, maximizing a windows maximizes it over both screens instead of just the one it is in.

---

### Post by mirzmaster on 2009-12-01
> **wetmonkey said:**
> Here is the bug I am watching/posting in launchpad
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378")

Thanks for sharing the bug id!  I've subscribed to this bug...

For those who haven't read the bug, there is a workaround given there.  Hold down the Alt key and middle mouse button on top of a window to resize it past the screen border.

Quite silly indeed...

---

### Post by alex2399 on 2009-12-03
> **mirzmaster said:**
> Thanks for sharing the bug id!  I've subscribed to this bug...

For those who haven't read the bug, there is a workaround given there.  Hold down the Alt key and middle mouse button on top of a window to resize it past the screen border.

Quite silly indeed...

Wow thank you very much! :D

Missed that comment. This way one is even able to stretch a window over multiple desktops! Great functionality that I didn't know about.

---

### Post by Kaput1982 on 2010-01-20
Thank you.  I have also noticed this problem, and it's nice to know there's a work around.

---

### Post by gerrywastaken on 2010-05-08
It's been 6 months now and this still hasn't even been assigned to anybody. If you guys haven't marked that this affects you on the bug, then please do so: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/455378)

Haven't been able to test this on Lucid yet as my duel screen setup is still using Karmic, but if anybody finds it doesn't work there then please also mark that under the affected distros.

---

### Post by AintJoe on 2010-05-28
The problem persists in lucid.

---

### Post by Jason Quinn on 2010-05-28
This appears to be Bug 1219 "Unable to resize across monitors on nvidia" at the Opencompositing Bugzilla. [http://bugs.opencompositing.org/show_bug.cgi?id=1219](http://bugs.opencompositing.org/show_bug.cgi?id=1219)

---

