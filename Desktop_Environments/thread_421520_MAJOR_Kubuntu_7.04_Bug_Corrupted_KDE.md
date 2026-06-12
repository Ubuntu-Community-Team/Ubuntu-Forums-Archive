---
title: "*MAJOR* Kubuntu 7.04 Bug Corrupted KDE"
date: 2007-04-24
forum: Desktop Environments
---

### Post by sb73542 on 2007-04-24
Hi,

I installed Kubuntu 7.04, and everything seemed normal.  I logged in and out, add/removed some programs, and all was well.  Then I installed the Knemo network monitor applet.  It didn't show up, even when I enabled it in Kcontrol.  So I tried logging in/out.  And from then on I could not log into my KDE.  It would get to the point of loading the desktop, then exit back to KDM.  I am able to load individual KDE apps from the failsafe login, but I can't get it to load the desktop when I run startkde from failsafe.  I re-installed, and tried again, and KDE again quit working after I installed Knemo.  I tried un-installing Knemo, but KDE remains broken.

---

### Post by jda1701 on 2007-04-25
This could have something to do with the fact that Feisty uses NetworkManager to manage the network connections now.  Trying to use Knemo might interfere with NetworkManager. 

Report the bug to launchpad ([https://www.launchpad.net](https://www.launchpad.net)) and don't use Knemo I suppose.

I hate recommending NOT using something but if it breaks your system at this time you might want to stay away from it until there is a fix available.

---

### Post by sb73542 on 2007-04-25
Hmmm, I don't think the problem is NetworkManager.  Mandriva 2007.1 also uses NetworkManager and Knemo works fine with it.  Knemo is just a monitor, it doesn't control any interfaces.  At the very least, the entire KDE installation shouldn't be broken by a bad package.  Maybe I'm totally wrong and it's some other problem that I happened to experience twice in a row.  But it appears that Knemo is the culprit.

Here's the bug: [https://bugs.launchpad.net/ubuntu/+source/knemo/+bug/109818](https://bugs.launchpad.net/ubuntu/+source/knemo/+bug/109818)

---

