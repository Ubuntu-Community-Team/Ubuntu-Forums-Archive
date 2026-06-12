---
title: "[SOLVED] E1405 wlan Driver"
date: 2007-08-29
forum: Dell  Ubuntu Support
---

### Post by doublearon on 2007-08-29
Hey guys, I'm pretty new to Linux in general but I'm pretty good at following directions. I followed the Howto here for a 1505 (even though I have an e1405) seeing as though the 1505 also has the 1390 card: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

almost exactly, with a CD command that I missed (but later corrected my error). I got all the way to the end, where it says

root@qulaptop:/windriver/DRIVER# sudo ndiswrapper -l
bcmwl5 : invalid driver!

I went to Dell's support site, and come to find out the 1405's .exe driver file is a different file name  when compared to the Howto. The howto calls for R15151**7**.EXE, while Dell says to use R15151**9**.EXE.

So I went through the Howto another time, followed the instructions exactly with the Dell prescribed .exe and it still gives me the invalid driver! message. 

Also, in step four of the tutorial, I can't see any interaction with ndiswrapper and the extraction of the driver (R15151**9**.EXE). Should I be extracting the R15151**9**.EXE in to the DRIVER folder of ndiswrapper? Is there a command that's missing to make ndiswrapper associate the extracted drivers?

I'm pretty stuck at this point. 

Maybe I just answered my own question because the only thing I can think to do is to actually place the contents of the extracted .exe inside of the DRIVER folder of ndiswrapper. 

Thank you so much in advance for letting me pick your brains!

-Double A

Edit: I'm running Ubuntu Fiesty 7.04

---

### Post by doublearon on 2007-08-29
It may be of interest that Dell says "	Download this driver if you reside in the US. " for the R151519.exe

---

### Post by doublearon on 2007-08-29
Well, I did a heck of a lot more reading and I fixed it. It's one of those things where you think you know what you did, but you're not *quite* 100% sure. 



I looked at this guy's eppifany and realized I might have the wrong driver after seeing a few more talk about their success with the same machine/wifi card.
[http://www.linuxquestions.org/questions/showpost.php?p=2671393&postcount=5](http://www.linuxquestions.org/questions/showpost.php?p=2671393&postcount=5)
 But in the end, I used the HOWTO on these forums combined with his advice. Total time spent: 3.5 hours :D

---

