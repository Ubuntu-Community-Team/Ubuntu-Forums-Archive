---
title: "apt-get/aptitude not working"
date: 2006-03-05
forum: Desktop Environments
---

### Post by yumigator on 2006-03-05
I attempted to install VMware. I downloaded the tarball, extracted it, and ran the vmware-install.pl file. But being a complete Linux newbie, instead of doing
```
sudo ./vmware-install.pl
```
I did
```
sudo nautilus /home/yumigator/Desktop/vmware-player-distrib
```
and double-clicked the vmware-install.pl file, clicking on the "Run" button at the prompt. At this point, a whole bunch of text is speeding through my Terminal, instead of asking me questions. But I kept going, not thinking anything was wrong (and quite proud of myself for figuring out how to run Nautilus with Terminal :rolleyes: ). But after I finished reading the license agreement, it went through an infinite loop, asking me to say "y" or "n", and then saying "'' is not a valid response, you must choose 'y' or 'n'" or something like that.

Eventually, I found a guide, and learned about the "./". But now, whenever I run apt-get or aptitude, I get an error message saying "The package vmwareplayer needs to be reinstalled, but I can't find the package for it."

Anyone ever had this problem before, or know what to do? (This time, I'm determined not to have to clear my HD and reinstall Ubuntu, which so far, I've done 3 times, in a time frame of 4 days.)

---

### Post by o_fortuna on 2006-03-05
[QUOTE=yumigator]I attempted to install VMware. I downloaded the tarball, extracted it, and ran the vmware-install.pl file. But being a complete Linux newbie, instead of doing
```
sudo ./vmware-install.pl
```
I did
```
sudo nautilus /home/yumigator/Desktop/vmware-player-distrib
```
and double-clicked the vmware-install.pl file, clicking on the "Run" button at the prompt. At this point, a whole bunch of text is speeding through my Terminal, instead of asking me questions. But I kept going, not thinking anything was wrong (and quite proud of myself for figuring out how to run Nautilus with Terminal :rolleyes: ). But after I finished reading the license agreement, it went through an infinite loop, asking me to say "y" or "n", and then saying "'' is not a valid response, you must choose 'y' or 'n'" or something like that.

Eventually, I found a guide, and learned about the "./". But now, whenever I run apt-get or aptitude, I get an error message saying "The package vmwareplayer needs to be reinstalled, but I can't find the package for it."

Anyone ever had this problem before, or know what to do? (This time, I'm determined not to have to clear my HD and reinstall Ubuntu, which so far, I've done 3 times, in a time frame of 4 days.)[/QUOTE]
Have you tried running the installer again? ./ shouldn't have made a difference, by the way, I run stuff through nautilus all the time. And what was the question? Did you press y and then press enter, and it would just give you that message? Getting through the install is the best way to fix the package, unless you can find a .deb package for vmware-player, which you could install more easily with apt-get or aptitude.

---

### Post by yumigator on 2006-03-05
I did get through the install successfully, but apt-get and aptitude are still screwed up.

And although the ./ doesn't matter, running the file in terminal is still different than opening Nautilus in root, and running the file from there (well, it has to be, otherwise this problem wouldn't be there now). Running in Nautilus is the same effect as typing
```
#open vmware-install.pl
```
which is different than just
```
#vmware-install.pl
```
It wouldn't give me a chance to press 'y' and enter, it just kept cycling through the loop. Anyway, that's not the question, because I did get a successful install, running the file in terminal. The question is, how do I fix apt-get and aptitude so they stop giving me the vmware package error message?

Of course, I could just download deb packages and install from there, but apt-get is more convenient, if I can get it fixed. Any ideas?

---

### Post by yumigator on 2006-03-09
*bump*

Can anyone help? Or if I'm screwed... could you just tell me that?

---

### Post by %hMa@?b&lt;C on 2006-03-09
try 
sudo apt-get remove vmwareplayer

---

