---
title: "X Stops Responding To Mouse Events"
date: 2009-04-02
forum: Desktop Environments
---

### Post by mw007x on 2009-04-02
This is a duplicate of the launchpad bug filed here [https://bugs.launchpad.net/ubuntu/+bug/296167](https://bugs.launchpad.net/ubuntu/+bug/296167)

I am a Gentoo'er and am using Ubuntu at my job. I am having the problem described by the bug posted above quite frequently. I am using Xinerama for multiple monitors, and animated mouse cursors.

My question is, how do I tell which version of X.Org I actually have, and which versions can I install? Here is what synaptic tells me...

I have the following version of xserver-xorg installed: 1:7.4~5ubuntu3. What exactly does this mean? I know X.Org is currently at version X11R7.4 but the most recent post in the bug I've listed says the issue is fixed in upstream version 1.6.0? I've looked up and down synaptic and see nothing even remotely related to xserver and version 1.6.0

I've tried pointing synaptic to look at the development repositories (I think) but that doesn't seem to change anything, so maybe I'm already running the most recent versions of the code?

Any help is greatly appreciated.

mw

---

### Post by Giblet5 on 2009-04-02
Your choices are A) Upgrade to Jaunty, B) build a custom Xserver for your release after applying the patch, C) use no application that will call UpdateSpriteForScreen(), or D) wait for the backport.

Launchpad says it's fixed for Jaunty, and that the fix is "trivial", so you'd have to wait for the patch to float to the top of the heap for backports on your release of Ubuntu, if you want to stick with managed code.

Security patches always bump usability patches.

Or, you can build your own Xserver from current source for your release and fix it immediately using the patch linked on Launchpad as the starting point (assuming the patch won't apply cleanly from the start).

The animated cursors, while interesting for 5-7 seconds, are clearly exacerbating the problem. You may want reevaluate their benefit if you don't have the time to build a custom Xserver, although that is no guarantee that UpdateSpriteForScreen() won't be called by something else, like Flash or a game.

---

### Post by mw007x on 2009-04-02
From what I understand from reading launchpad, animated cursors help reproduce the problem, but are not the main cause. Or did I read incorrectly?

I'll disable them and see how that goes.

I could definitely compile my own X server, if this doesn't work.

Thanks!

---

