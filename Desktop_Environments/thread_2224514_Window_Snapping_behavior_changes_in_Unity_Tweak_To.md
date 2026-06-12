---
title: "Window Snapping behavior changes in Unity Tweak Tool not taking effect"
date: 2014-05-16
forum: Desktop Environments
---

### Post by ouff on 2014-05-16
I'm trying to change the window snapping behavior in Unity (14.04) using the Tweak Tool. The Window Snapping section of the tool is available, and all the options are available (not greyed out). I make the changes I want, but the actual snapping behavior doesn't change. For instance, I set the bottom screen edge to "Bottom Half", and then drag a window to the bottom edge and nothing happens. Closing the tweak tool, logging out and back in, and even restarting the whole computer don't help. After making a change, if I close and then reopen the Tweak Tool, the change persists. It's simply not reflected in the actual snapping behavior.

Any thoughts?

---

### Post by monkeybrain20122 on 2014-05-16
I am not sure if the unity tweak tool is any good. I always use the CCSM (CompizConfig Settings Manager) to make that kind of changes, but be careful, you desktop may go crazy while you are adjusting the settings and you'll need to reboot after. You need to install it from synaptic or software centre first though.

---

### Post by ouff on 2014-05-16
Thanks, that worked!

In case anyone else has this issue and stumbles across this post, here are the details. 

_Install CCSM_
From terminal: [FONT=Courier New]sudo apt-get install compizconfig-settings-manager[/FONT]
Or you can install it from the Software Center

After you install CCSM, open it up and go to:

Window Management -> Grid

Then click on the "Corners / Edges" tab and configure away.

---

