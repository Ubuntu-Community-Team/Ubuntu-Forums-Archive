---
title: "unity / dual monitor weirdness"
date: 2011-12-28
forum: Desktop Environments
---

### Post by teacherjeff on 2011-12-28
After much trial and error, I seem to have managed to configure an external monitor to work with my HP laptop running Ubuntu 11.10.  (The laptop has ATI graphics.)  I did this by running amdcccle from the command line and then configuring the two monitors.  Getting them both to work at the correct resolutions, and getting the desktop to extend across them too a lot of effort.  Especially since I don't especially know what I'm doing.

But all seemed to be good.  And once I activated xinerama (which I don't really know what is), I was able to drag applications from one screen to the other.  Which is, for me, kind of the point.  I don't want anything fancy, just more screen real estate.  So I can have, for instance, a couple of Office documents and a Firefox window all open and large enough that I can see them.

But then things started going wrong.  The Unity desktop seems to behave strangely, especially when I start maximizing windows.  For example, the launcher moves from one display to the other. Once or twice it disappeared completely and I had to restart to get it back.  Application menus disappear in unpredictable ways.

If I avoid maximizing windows, things seem to work okay.

And another point of weirdness: Now if I left-click on the little gear-looking thing in the panel at the top of the screen (which would usually give me a dropdown menu with options to turn off, hibernate, etc.), that menu only appears as long as I hold down the mouse button.  Before a click would make it stay around so I could click on one of the options.

I think I'm caught between the ATI screen configuration software, X, xinerama, Unity, and compiz.  (Note that my understanding of each of those terms is incomplete.)

I apologize for the unclear terminology: I'm still fairly new at this.  

But any guidance?  General pointers?

Thanks.

---

### Post by Risk_3715 on 2012-11-27
The last problem reported in teacherjeff's post is the problem I'm experiencing. I first configured my screens in their relative space using amdcccle display manager. And to utilize my third monitor, I turned on Xinerama. After the reboot, clicking menu items will only display as long as I hold the mouse button down.

I was wondering if anyone else has experienced this?

Running 12.04LTS 64 bit, i5 750 chip, 2x ati 5770's

---

