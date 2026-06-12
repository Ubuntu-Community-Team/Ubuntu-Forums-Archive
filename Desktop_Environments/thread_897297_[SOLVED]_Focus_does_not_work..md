---
title: "[SOLVED] Focus does not work."
date: 2008-08-22
forum: Desktop Environments
---

### Post by kennybob on 2008-08-22
I'm in firefox, and I point up to my top panel, to click on a Command prompt. The window is open, but the focus doesn't go there.

I am running Thunderbird, and I try to run Synaptic. The dialog comes up and asks me for my password. (Its not really in Focus, grayed out box), but I can type in it. After I press enter, the focus still doesnt go to Synaptic, I'm still looking at Thunderbird.  If I try to open a window to compose a new letter, the focus doesn't go to that box, I have to click on the button on the bottom panel. 

I'm looking at my desktop. Nothing is running. I click to open a command prompt. The window comes up but it is grayed out, and the button on bottom panel is flashing.

I run my Sound Preferences dialog, and try to go into System Monitor. It runs, but can't see the whole thing cause its behind the Sound window. The button on the bottom is flashing.

Do you see the problem.  I don't have the infamous focus stealing thing going on. I have no focus going on.  I wish something would steal the focus.

Please help. This is getting ridiculous.  I'm going mad trying to deal with typing into thin air sometimes.

Thanks

---

### Post by kennybob on 2008-08-22
I figured it out, but I don't know why I had to do it this way.  I do not have compiz installed. No effects whatsoever. 

After looking in some past posts, I came upon this one:

[http://ubuntuforums.org/showthread.php?t=850895&highlight=focus](http://ubuntuforums.org/showthread.php?t=850895&highlight=focus)

It seemed like the exact problem I have. So I tried to run ccsm, and it said it wasn't installed.  So just for the heck of it, I installed it.  It didn't install compiz, just the config manager.

I went to General - General Options - Focus and Raise Behavior - and turned off Focus Prevention Level.

Now everything works like it used to.

---

