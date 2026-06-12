---
title: "minecraft help - black screen"
date: 2015-07-17
forum: Gaming &amp; Leisure
---

### Post by jack151 on 2015-07-17
got this black screen issue and now i get a crash report too (lucky me) and i have no clue whats going on lol, im not very good with computers, mainly just linux lol, so if you can help please go through everything simple for me as i dont understand it lol thank you all ill post a paste bin below of my crash report if it helps :) thanks


Pastebin link : [http://pastebin.com/fwNx29pi](http://pastebin.com/fwNx29pi)

---

### Post by efflandt on 2015-07-17
Looks like a graphics issue (GL). How much total RAM does that computer have and assuming it only has Intel graphics, what does the following show entered in a terminal window ```
lspci | grep VGA
```If it is pre-HD Intel graphics good luck (even if it does run it may be slow). I have never run minecraft with Oracle Java (just openjdk-6 or 7 -jre), so not sure what some of those java options mean.

---

### Post by jack151 on 2015-07-17
when i put that code in the terminal this is what i got : 

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by sgian on 2015-07-24
It looks like your graphics are better than anything I have, according to the following intel page:  [http://ark.intel.com/products/53490/Intel-Pentium-Processor-G840-3M-Cache-2_80-GHz](http://ark.intel.com/products/53490/Intel-Pentium-Processor-G840-3M-Cache-2_80-GHz)

I don't understand everything in the log, but I have two things I thought of while looking it over...
1. Java is up to 1.8.0_51 now.  If you are using webupd8 to keep java up to date, you might have to wait a while.  Personally I gave up on them and got rid of the webupd8 PPA to install the current java.
2. I agree that it appears to me to be a driver issue.  I had trouble with 15.04 and went back to 14.04 LTS and now Minecraft runs fine with java for me.
3. Or you might try finding a supported graphics card with proprietary drivers, I have found that using proprietary drivers seems to work better for me with Minecraft and all the mods my kids try to run, then to rely on the opensource drivers.

---

