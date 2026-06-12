---
title: "Multi Monitor Issues"
date: 2011-05-17
forum: Desktop Environments
---

### Post by f1sheyes on 2011-05-17
Hi all,

Posting on iPhone so will be brief. Installed 11.04 yesterday instead of windows 7 and am having issues with multiple screens. Currently I have screens 0 and 1 combined and screen 2 as a separate x window. These are nvida cards and I am using the nvida GUI frontend which appears to edit Xorgs.conf. Screen 0-1 work fine together however I can find no way of starting apps on screen 2 (i can drag the mouse into the screen) I assumed I would have to change  the display variable but no luck so far. Can anyone help me out please? Ideally I would have the session spread across all three but this was not availbe from the GUI.

Thanks for your time.

---

### Post by gsmanners on 2011-05-17
In a separate X screen, you really should create a launcher in that screen. That way, you just run from that launcher to get the app in that screen. I'm not sure how you do that with Unity, but I suppose you should be able to use Nautilus (the Desktop) to just create icon launchers wherever you want.

---

### Post by Copper Bezel on 2011-05-17
Synapse might also be a suitable option, since it would mean at that you could keep the desktop clean. It's like a beefed-up semantic Run Dialog (and damned responsive at that.)

```
sudo add-apt-repository ppa:synapse-core/ppa
sudo apt-get update
sudo apt-get install synapse
```

I don't think there are any docks or launchers that can be arbitrarily tied to one display or another the way Gnome Panel could be.

---

