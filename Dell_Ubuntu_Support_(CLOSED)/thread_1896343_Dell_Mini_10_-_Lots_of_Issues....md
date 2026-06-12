---
title: "Dell Mini 10 - Lots of Issues..."
date: 2011-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by moseswynn on 2011-12-16
Hi there! I am helping one of my friends fix her computer and I have encountered quite a bit of problems... She has a Dell Mini 10 that had the Jaunty Netbook Remix installed on it. One day it decided not to boot up so she had me completely reinstall. First I tried installing the newest NBR but it was always freezing on the install screen, so I just ended up reinstalling Jaunty.

The first problem came when I tried to perform updates after installing it was that none of the lists for the software repositories can be read.

Secondly, I tried to install Flash Player from the software sources and it said that it could not install because the software didn't support the i386 filesystem.

Also, some of the programs that came preinstalled with Jaunty, like Rhythmbox, aren't working.

Any help with these issues would be greatly appreciated!!! Thank you very much!

---

### Post by mikewhatever on 2011-12-17
Dell had several different 10 inch minis, all confusingly called Mini 10. Can you post the output of **lspci** to identify the model and the hardware in question.

Jaunty was released in April 2009 and reached End of Life in October 2010. What newest NBR have you tried? 10.04?

---

### Post by ugm6hr on 2011-12-18
I would suggest not using NBR - but just any standard 32-bit (i386) version of Ubuntu. I've very recently put Mint 12 on my Mini 9.
As mentioned although wifi and graphics chipsets have varied between versions - so the lspci output is important for us to know about. However, if it came preinstalled with Ubuntu, I'd be surprised if it came with GMA 500 chipset, which is the only one I'm aware of that caused major problems.

---

