---
title: "Login issue Ubuntu 12.10 on BeagleBoard Xm"
date: 2013-04-04
forum: Education &amp; Science
---

### Post by ThaHypnotoad on 2013-04-04
Hello. Im new to the entire linux thing, so if I have overlooked something REALLY obvious i urge you not to flame me. I had recently made an ubuntu 12.10 image for my beagleBoard Xm rev C. It booted correctly. The regular terminal seemed to be fine. I was even able to install the GUI. The problem came when I attempted logging in through the GUI. I typed in the standard username and password  ubuntu : temppwd. I clicked the login button and it greyed out, as if the login had worked, but then it just stayed at that screen, with the login button greyed out. 

I used instructions from [this]("http://www.brianhensley.net/2013/01/beagleboard-xm-how-to-install-ubuntu.html") blog. I skipped the SPI step as it didn't seem to recognize the command and the page said it was optional. Otherwise, I followed the instructions word for word.
 
I hope that this is just me being a newbie, but thanks in advance to whoever will help me.

---

### Post by Avinash Koushik on 2013-04-28
Hello,

I too have the same problem. Did you find any solution?

With regards,
Avinash

---

### Post by Sef on 2013-04-29
> [COLOR=#000000]Hello. Im new to the entire linux thing, so if I have overlooked something REALLY obvious i urge you not to flame me.[/COLOR]

If someone does flame you, please click the Report Post button (bottom left) and the Ubuntu staff will deal with the offender.

From the[ Ubuntu Code of Conduct 1.3]("http://ubuntuforums.org/misc.php?do=showrules"):

> **Trolling, Attacks and Flaming: These are always forbidden.**

---

### Post by Avinash Koushik on 2013-04-30
Hello,

I was able to solve it. If you run startx from your serial port you might get something like this :
[FONT=arial]"failed to load session "gnome" " . Hence you need to install gnome again. You can go through this thread : [/FONT][http://ubuntuforums.org/showthread.php?t=1750430](http://ubuntuforums.org/showthread.php?t=1750430)

Then when you try logging in with your user name you might get a message saying not able access ICEauthority. Hence give permissions for the same. You can try instructions in the following thread:
[http://ubuntuforums.org/showthread.php?t=1841457](http://ubuntuforums.org/showthread.php?t=1841457)

With regards,
Avinash

---

