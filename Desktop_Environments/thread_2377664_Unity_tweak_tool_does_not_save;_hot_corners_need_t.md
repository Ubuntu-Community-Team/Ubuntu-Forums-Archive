---
title: "Unity tweak tool does not save; hot corners need to die"
date: 2017-11-15
forum: Desktop Environments
---

### Post by somerandomguy2 on 2017-11-15
I'm on a simple quest to kill hot corners on a stock 1604 install. The Unity tweak tool has a really neat switch that... uh... does nothing. Exiting and going back in shows that the hotcorners function is still enabled. 

This is as a standard user (I assume sudo would change it for root only) and no errors anywhere that I can find, much less from the GUI tool.

I am fine with directly editing any config data if the tool doesn't work for this version... just need a pointer where. 

TIA

---

### Post by deadflowr on 2017-11-15
Hot corners?
There are no hot corners on a default setup of Ubuntu 16.04.
You have to manually set those yourself.

Are you sure it's unity, the default Desktop session of Ubuntu 16.04 and not something else?

What happens when you press against the hot corner?

---

### Post by somerandomguy2 on 2017-11-15
> **deadflowr said:**
> What happens when you press against the hot corner?

Assume I have a full screen window... clicking anywhere NEAR the upper right corner activates the system menu (e.g. what normally has the power button, with system settings, log out, suspend, shutdown, etc). 

The tweak tool thinks it is "on"... I apologize for ignorance if the behavior is something different.

---

### Post by deadflowr on 2017-11-15
What is the hot corner setting for that pesky right corner?
There are a limited few options, such as show workspaces spread all windows, toggle desktop, and window spread along with the default disabled.

I'm also curious about the clicking on the area behavior, since tweak tool's hot corner setup only allows hover meaning you hover the mouse into the corner and it invokes the hot corner setting you've set. Or at least as I can tell.
That particular ability (clicking on the hot corner) can be set in ccsm (compizconfig-settings-manager) though.

---

### Post by somerandomguy2 on 2017-11-16
Wow, thank you, did not know about ccsm. 

That said, I'm not seeing anything that looks like a setting that could control clicking or move it to a different location... what is it called?

---

