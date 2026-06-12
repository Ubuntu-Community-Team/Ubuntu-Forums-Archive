---
title: "Faster Workspace switching effects"
date: 2012-07-27
forum: Desktop Environments
---

### Post by najdorfchess on 2012-07-27
Hi all. I use Ubuntu 12.04 extensively in a software development environment and the workspace feature is a bliss when it comes to handling open windows.  I only have one monitor in my workspace, so I usually keep different category windows in different workspaces (like browsers in one workspace, terminal in another, open documents in another etc.). 
I also have configured my keyboard shortcut (Alt + Arrow keys) to switch between workspaces but the only annoyance is that everytime I make a switch it brings up this animation feature containing the four mini windows along with the slide effect which kinda gets annoying when you switch between workspaces very often. 
Also the small square windows stays on the screen for a couple of seconds which is another thing i wanna get rid of to improve my working speed and productivity. I have included a screenshot of what i mean. If anyone knows how to change this, please let me know. 

I was searching at Compiz CSS but couldnt find a proper solution for my problem. 

[[img]http://s14.postimage.org/qoj5uoqm9/Screenshot_from_2012_07_27_13_07_49.png[/img]](http://postimage.org/)
[image host](http://postimage.org/)

---

### Post by stinkeye on 2012-07-27
The default workspace switcher uses the compiz **desktop wall** plugin.

Use ccsm to change the appearance.
Install ccsm...
```
sudo apt-get install compizconfig-settings-manager
```

Press alt+F2 and type in ccsm.
Navigate to ccsm > Desktop > Desktop Wall

Then change the appearance as shown.
[ATTACH]221888[/ATTACH][ATTACH]221889[/ATTACH]

You may also find the [**_[COLOR="DarkRed"]indicator-workspaces[/COLOR]_**]("https://launchpad.net/~noobslab/+archive/indicators/+files/indicator-workspaces_0.6.4_all.deb") handy.
[ATTACH]221890[/ATTACH]

---

### Post by najdorfchess on 2012-07-30
That helped thanks a lot!  :-)
Marking this thread as solved.

---

