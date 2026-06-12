---
title: "trying to install the java plugin for firefox"
date: 2005-12-03
forum: Desktop Environments
---

### Post by lmellen on 2005-12-03
:( I read the wiki on installing the jre. I'm not sure that I didn't make a mess trying to add the multiverse repository. I think I left part out,fixed it after I tried to install the jre.
I think I've cleaned up most of it, but I keep getting this error message after:
 " sudo apt-get fakeroot java-package java-common".
The message:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Totally lost!! Could use some assistance. --Thanks Larry

---

### Post by elempoimen on 2005-12-03
It's not a java problem.  It's an apt problem.  Do you have any graphical package manager open while running the apt-get command?  If so, close it and try again.  (KPackage, Synaptic, Kynaptic, Adept, etc...)

---

### Post by sanguinemoon on 2005-12-03
Yeah, it sounds like something else is using apt. I just installed the java plugin through Synaptic myself.

---

### Post by lmellen on 2005-12-03
:confused: As far as I can tell, nothing is open. I rebooted and now I'm getting:
                               "E: couldn't find package java-package" 

I 'm using adept, and as far as I can tell all the repositories are upgraded and enabled.
I also used ./ to open the jre, now I have two files:
                                                                   jre1.5.0_06
                                                                   jre-1_5_0_06-linux-i586
               
                                                                   Thanks for the replies --Larry:)
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I've probably spent the last 8 hrs trying to get the java plugin working. No luck. Still one final solution. I've upgraded, updated, upchucked, and everything else you can think of to the repositories, and I still get something about not being able to find the java-packages??????????
Anybody know what's going on with that??? -- thanks again - Larry
-------------------------------------------------------------------------------------------------------------------------------------------
Installed Ubuntu -- Much Better system!!! Everything works.

---

