---
title: "Getting more debug info from Nautilus"
date: 2007-06-09
forum: Desktop Environments
---

### Post by mikedawson on 2007-06-09
Hi Guys,

I'm having a really strange issue with Nautilus that I've googled for but can't find an adequate answer for - but also having some difficulty in trying to get some more debug info from Nautilus so that I can do a little more to diagnose the problem.

If I open the Documents folder (which has more shedload of documents) Nautilus will crash on the next folder opened.

It will then create the following output infinitely repeating the debug log dumped due to signal 8 line until it is killed.


(~/nautilus-debug-log.txt)

===== BEGIN MILESTONES =====
0x8934090 2007/06/09 20:02:09.9117 (GLog): offsetBlur not found

0x8934090 2007/06/09 20:02:09.9125 (GLog): offsetBlur not found

0x8934090 2007/06/09 20:02:09.9132 (GLog): offsetBlur not found

0x8934090 2007/06/09 20:02:09.9139 (GLog): offsetBlur not found

0x8934090 2007/06/09 20:02:09.9144 (USER): debug log dumped due to signal 8
0x8934090 2007/06/09 20:02:09.9147 (USER): debug log dumped due to signal 8
0x8934090 2007/06/09 20:02:09.9148 (USER): debug log dumped due to signal 8


(end ~/nautilus-debug-log.txt)

I also then looked for ways to try to increase the verbosity of the logging in the hope that I can get some more useful output - however I couldn't see anything in man nautilus, or on the nautilus page on gnome, or googling.

So does anyone know how can I get some more debugging output or how can I get to the bottom of why this folder causes the next folder opened to crash?  Interestingly enough I just moved to a new laptop - previous laptop was running Ubuntu 6.10 - and it was fine...

Regards,

-Mike

---

### Post by needtolookatascreenshot on 2007-06-10
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

