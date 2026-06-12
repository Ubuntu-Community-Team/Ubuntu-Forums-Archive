---
title: "External monitor (sometimes) on XPS 1330M"
date: 2010-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drmarkandersen on 2010-11-02
Moderately frustrating problem:
I have an external monitor (Sony SDM-S93) in my office that I like to use with my XPS-1330M laptop. Under Vista, I was able to do a couple of quick things in Control Panel and extend my Windows desktop onto this monitor. I could also easily disable the extended display while working at home (without an external monitor). I can't for the life of me figure out how to get this to happen with Ubuntu. I've used the built-in configuration tool (System -> Preferences -> Monitors, then elect not to use the graphics driver vendor's tool), the NVidia configuration tool (System -> Preferences -> Monitors, let "NVidia X Server Settings" handle it), and the Multiple Screens tool (under System -> Administration). The best I've been able to do is to get a desktop to show up on the Sony monitor (using the NVidia X Server Settings tool). I can freely move the cursor across both screens, but can't move an open window from the laptop's built-in display to the external monitor and back. I'd appreciate any help I could get in getting this to work for me.

---

### Post by bobcollard on 2010-11-02
See the following discussion over a similar project.  It seems you need KDE Desktop to accomplish this.

[http://ubuntuforums.org/showthread.php?t=1610402](http://ubuntuforums.org/showthread.php?t=1610402)

---

### Post by drmarkandersen on 2010-11-02
bobcollard:
Thanks, the thread you referred me to did help. Apparently, though, I don't have to switch from Gnome to KDE. Rather, I just need to enable "Xinematic" when I set up the second monitor in the NVidia configuration too. I'm still trying to figure out how to switch easily back and forth between the two setups on the fly, without rebooting, but since Ubuntu boots up so quickly, maybe that's not an issue.

While I'm thinking of it, though, is there a way to reset X from the command line?

---

### Post by bobcollard on 2010-11-02
> **drmarkandersen said:**
> bobcollard:
Thanks, the thread you referred me to did help. Apparently, though, I don't have to switch from Gnome to KDE. Rather, I just need to enable "Xinematic" when I set up the second monitor in the NVidia configuration too. I'm still trying to figure out how to switch easily back and forth between the two setups on the fly, without rebooting, but since Ubuntu boots up so quickly, maybe that's not an issue.

While I'm thinking of it, though, is there a way to reset X from the command line?
I don't know, you might google it or search the forums.

---

