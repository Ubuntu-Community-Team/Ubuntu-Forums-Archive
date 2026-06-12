---
title: "CMap Tools in Unbuntu"
date: 2008-08-04
forum: Education &amp; Science
---

### Post by artdijk on 2008-08-04
LS,
When I start the program I get two blank windows, so unable do do anything. Is there something wrong with the instal or what ?
Thanks,
Arthur
(NB New to linux )

---

### Post by goldfishoptics on 2008-09-25
hello artdijk,

i have the same problem. Install seemed to work fine.

Worked out how to solve it?

goodluck
goldfishoptics

---

### Post by davidgroos on 2008-12-22
I have exactly the same problem.  

So then I tried to apt-get java as this program is based on java but this didn't seem to affect the problem.  I've used this program for years on the Mac but am trying to upgrade to Ubuntu.  thanks

David

---

### Post by yothere on 2009-01-10
I'm also having the same issue and have had to resort to using my old machine to work on this program. 

My installation of JRE is fine, the most updated version. 

I can click on an imaginary button within the "Untitled 1" window. It's on the upper portion of the window and it opens a context menu with little options and such. 

If you double click a blank space in that same window another tool box appears with some options for what I guess would be the little thought bubble you've just created.

That's as far as I've gotten. I've tried [this]("http://ubuntuforums.org/archive/index.php/t-306784.html") and it didn't work.

---

### Post by yothere on 2009-01-10
I found the fix online [here]("https://answers.launchpad.net/ubuntu/+question/18055").

this is what it says:
Hello everybody,

I just came across the same issue with CmapTools 4.16 on Ubuntu 7.10. It seems as if the JRE which comes with CmapTools somehow causes the messed up GUI. Simply renaming/deleting the bundled JRE ("jre" folder in "IHMC_CmapTools/") solved the problem for me.

My Java version installed via Synaptic is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

Best regards,
Markus

---

### Post by ollenotna on 2009-11-04
> **yothere said:**
> I found the fix online [here]("https://answers.launchpad.net/ubuntu/+question/18055").

this is what it says:
Hello everybody,

I just came across the same issue with CmapTools 4.16 on Ubuntu 7.10. It seems as if the JRE which comes with CmapTools somehow causes the messed up GUI. Simply renaming/deleting the bundled JRE ("jre" folder in "IHMC_CmapTools/") solved the problem for me.

My Java version installed via Synaptic is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

Best regards,
Markus

Markus K solution (delete jre map) worked with CMAP 5.03 and Ubuntu 9.10.
Other messages pointed out an incompatibility between Cmaps/Jre and Compiz, but this is not the case: I have Compiz working and I didn't have to turn it off.

---

### Post by Nosferax on 2009-12-10
The fix worked for the main drawing window, however it seemed to corrupt the View window which was fine when I used their JRE. That window is now blank at first and the items draw themselves as I mouse over the buttons, not quite what you'd call usable.

Has anyone encountered this issue as well?

---

### Post by DHell on 2010-01-05
Hi,
Installed CMapTools 5.03 in Ubuntu 9.10 and had a similar problem: program loaded fine, the "navigator" window worked, but the "map" window was empty/inactive. Installed sun-java6-jre, but nothing changed. Then, renamed the jre folder under IHMC_CmapTools/ and the problem was solved. No further fixes were needed. Thanks Markus and ollenotna.

---

### Post by renareto on 2010-01-29
:-0 INCREDIBLE !!!!!
thx DHell !!! icredible...

Renato

---

### Post by YesSir on 2010-02-01
Confirmed, I changed the name of the jre directory and it works. Thanks!

---

### Post by rimshot4 on 2010-02-02
I used the same fix. EXCELLENT program.

The only problem I still run across is the inability to get the default open/save directory to change. I like to save docs to my UbuntuOne folder for easy syncrhonization, but whenever I try to change the default folder in Prefernces, it never "sticks" for longer than a session. I don't know if this might be related to the fix.

---

### Post by birdsarah on 2010-03-10
Same fix worked for me too.

Cmap 5.03 on Ubuntu 9.10

Installed and then changed directory name of jre under Cmap directory.

THANKS :KS

---

### Post by Method X on 2010-03-10
I faced this problem at winter school this year. You can just delete jre folder inside of CMap tools.
And its better to use sun-java package.
;)

---

### Post by Orion8 on 2010-03-24
Renaming the folder just makes it inaccessible to the program.  That is, deleting is a better idea as it frees up that space on your hard drive.  Unless you think you'll want the contents of that folder again someday...

---

### Post by Jorge_C on 2010-05-05
Same issue, same solution. CMapTools v5.03 installed fine, but the map screen was grey/empty. I deleted the jre directory, and now it works fine.

The developers seem to [http://cmapforum.ihmc.us/viewtopic.php?f=3&t=60&start=0]("http://cmapforum.ihmc.us/viewtopic.php?f=3&t=60&start=0") about this issue, it's some kind of compiz incompatibility.

By the way, if you happen to need CMapServer to do some collaborative work, deleting the jre directory won't work. You should follow the instructions provided in the link.

---

### Post by Livos on 2010-06-04
Thanks for the advice... worked for me just fine with Cmaptools 5.03 on Ubuntu 10.04, whereas the proposed way in the "FAQ" on the IHMC-support page [[CmapTools  on Linux presents a blank (grey) cmap window]("http://cmapforum.ihmc.us/viewtopic.php?f=3&t=60")] did not. 

Cheers, L
[]("http://cmapforum.ihmc.us/viewtopic.php?f=3&t=60")

---

### Post by GracaOnFire on 2010-10-21
Fix also worked for me. Ubuntu 10.04 and cmapLite 5.04

Thanks

---

### Post by Lylex11 on 2010-12-20
Great, thanks worked well on the maps window which was blank before. Now I'm having strange behaviour on the navigation window, same as a previous comment - the window is blank but draws itself when I mouse_over. Thanks again, now it's useable.

---

### Post by Lylex11 on 2010-12-20
Well, wait, I tried the link given above [http://cmapforum.ihmc.us/viewtopic.php?f=3&t=60&start=0](http://cmapforum.ihmc.us/viewtopic.php?f=3&t=60&start=0) and now all windows are up and running. This is a better fix for me. Ubuntu 10.10 and running CmapTools 5.04.01

---

### Post by kayagokhan on 2012-02-01
Dear All,
I  deleted jre file in the cmap folder, and checked out java version for ubuntu 11.10

java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)


but cmap is not available thought I completed installation.

Appreciated with any helps

---

