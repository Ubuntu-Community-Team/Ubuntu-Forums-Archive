---
title: "Minimised Windows cause large cpu load"
date: 2013-10-30
forum: Desktop Environments
---

### Post by viking777 on 2013-10-30
I have had this problem for several days now, I haven't seen anyone else reporting it, and I haven't been able to solve it. 

Ubuntu Unity 12.04 LTS fully updated. Runs perfectly all the time - until I minimise ANY application window. As soon as I do that the cpu load and temp shoot through the roof and the desktop becomes nearly unusable. The culprits, as shown by 'top' in conky are Compiz, Xorg, Unity and the minimised application (and sometimes bamfdaemon as well). If I can find a cpu cycle in which to close the minimised window everything quickly reverts to normal. If I don't minimise any windows there is no problem - I can leave as many open windows as I like (i5 processor, 6Gb ram).

I have tried downgrading compiz and unity to no effect, and downgrading xorg resulted in a non bootable system. 

I have very few compiz effects enabled, and although my desktop shows conky and docky killing both of those has no effect whatsoever on the problem. 

Any ideas? 

I will check in tomorrow to find out.

PS I have two other distros on the same machine both of which run normally (although neither of those uses compiz).

TIA.

---

### Post by viking777 on 2013-10-31
Ok found the cause. I had been trialling a program called 'Synapse' which does a similar job to the Unity dash, and does it very well incidentally. When I removed this program the cpu race stopped. 

This trial is in preparation for me ending my acquaintance with Unity over lack of dodge windows and 'scopes' spyware. 

In case you didn't know most of the best features of Unity can be attained by using Docky (replaces the laucher but with dodge windows/intellihide function still intact), Synapse (replaces the dash search minus the spyware) and Zeitgeist (which aids Synapse). Just add these programs to some other form of 'buntu or one of its clones. The only features you will lack are the HUD, which imho is a good thing because it is a complete waste of space, and quicklists, which is a shame because they are brilliant, although the docky programmers do say that they are on their list of things to implement in the future. Don't hold your breath though as the pace of development in that particular program is not exactly fast.

Good luck and thanks for all your help;)

---

