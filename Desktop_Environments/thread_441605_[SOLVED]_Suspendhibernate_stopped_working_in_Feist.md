---
title: "[SOLVED] Suspend/hibernate stopped working in Feisty"
date: 2007-05-12
forum: Desktop Environments
---

### Post by highfructose327 on 2007-05-12
Suspend/hibernate stopped working for me, when I first upgraded to Feisty it was spot on. Now it does not work and I have been unable to turn up any good search results on a fix. All I get is the generic Message: Suspend Problem, your computer failed to suspend check the help file for common problems. which the Help file tells me : When a suspend failure occurs you may get this following warning. The most common reason for this notification is that the current user does not have permission to suspend or hibernate the computer. Great if that is the issue how and where do check to see if I have permission?
 I am able to hibernate with in terminal but not from the desktop interface, so I thought i would try suspend from terminal.It did not suspend here is what I got from terminal

> $ sudo echo mem > /sys/power/state
bash: /sys/power/state: Permission denied




---

### Post by highfructose327 on 2007-05-13
There must have been a conflict, I went into synaptic did a search for"suspend" removed three packages with  a relation to suspend/hibernate, and after that suspend/hibernate works fine. I loaded the Kubuntu-desktop package a while back  to see what KDE was like maybe I caused a conflict because of this not sure. Happy to get suspend back in order though. \\:D/ 
problem solved

---

