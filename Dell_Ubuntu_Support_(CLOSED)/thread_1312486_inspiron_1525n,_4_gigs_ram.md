---
title: "inspiron 1525n, 4 gigs ram?"
date: 2009-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bryncoles on 2009-11-03
Hi all. Once upon a time, I bought an Inspiron 1525n with Ubuntu pre-installed from Dell (and it was even cheaper - just - than the windows version!). Now, I got one with 4 gigs of ram, and with the release of Karmic, I have finally updated to 64 bits (and ext4). I am very happy with it...

... except, the command 'free -m' tells me i have a total of '3010' memory. Meanwhile, the bios tells me I have 3072 installed and 3062 available (as some is reserved for the computers own operations). 

My question is this: am I missing something? IE losing some ram, and is there something I should do to resolve the issue?

Cheers in anticipation guys!

---

### Post by leedsdevil on 2009-11-03
wow im running similar specs and im reading 3.4 gigs ram but im also using the 32 version of Jaunty 9.04 interesting to see if i upgrade to the 64 bit version sorry i do wish i could help you further

---

### Post by mpsii on 2009-11-03
If the BIOS says you don't have 4GB, then either there is a configuration option you have not selected, bad memory chip, or a hardware limitation.
 
Do this:
 
1) try MEMTEST to check the ram
2) switch the sticks of RAM and see if anything changes
3) Try each stick of RAM in each slot, individually and monitor the BIOS
4) Check the video card settings in the BIOS and determine exactly what the video card is using.
 
Before the OS can see it, the BIOS has to read it as 4GB (less video ram or other chipset needs). I cannot believe that the laptop video card and chipset are using 1GB of system RAM.

---

### Post by bryncoles on 2009-11-04
cheers - I'll try that this evening, and see what I can achieve. I'll post back when I know something!

---

