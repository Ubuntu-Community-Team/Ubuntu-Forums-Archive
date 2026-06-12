---
title: "Freezing issue"
date: 2009-05-02
forum: General Help
---

### Post by d_breidegam on 2009-05-02
I recently upgraded from 2gb to 4gb of ram in my computer and it seems prevent using ubuntu. I originally had 32bit ubuntu 9.04 on (upgraded from 8.04) and after the login screen appears and i login it freezes after about 2 minutes of use. If i dont login it freezes the login screen. I thought that the ram might be the issue so i checked by booting windows (i dual boot) which is 32bit windows xp sp2 and that worked perfectly fine, showed 3.28 gb of ram in system properties. I ran the memtest and for 2 hours it showed no errors. So i went into recovery mode and ran the dpkg and the xfix thinking that since the crash occurs only when running X that its a graphical issue. It did not work. Since i want to utilize all 4 gigs i grabbed 9.04 ubuntu 64bit and installed it. The install went fine but afterwards the same problem was there. Im unsure of how to proceed from here so anyone have any suggestions? here are my hardware:

Biostar TF570 SLI motherboard
DualCore AMD Athlon 64 X2, 2800 MHz (14 x 200) 5400+
NVIDIA GeForce 8600 GT  (256 MB)
Belkin Wireless G USB Network Adapter 
4 gb (4x1gb) DDR2 ram
500gb SATA hdd with 4 partitions (windows, ubuntu, storage, swap)


and thanks in advanced for the help guys.

---

### Post by coffeecat on 2009-05-02
This does sound like the new RAM is faulty. Linux utilises available RAM in a different way from Windows and is much more likely to reveal a fault in RAM than Windows. Also, you need to run memtest for much longer than 2 hours to be sure that you haven't got faulty RAM. The longer you run memtest without errors, the more certain you can be that your RAM is good, but you you can never be 100% sure.

---

### Post by codeseer on 2009-05-02
Get an 8.10 live CD, boot it up and see if it crashes in the live CD mode. If not, then your problems are probably related to Jaunty. If you have problems with 8.10, then I'd say take all but one memory stick out of the system and try again, then add another and so forth until you get the issue again. It could be one stick, multiple sticks, a slot issue or something else.

Also, grab the system temperatures if you can; processors, graphics card, etc.

---

### Post by d_breidegam on 2009-05-02
the temps do not appear out of the ordinary (23 C for processor, 30 C for hdd, 33 C for graphics) grabbed them before it froze. I thought at first it was a ram problem but 2 things lead me to believe that its not the fact that its the ram but the fact that im using 4gb. The ram was lightly used by a friend who also used them under ubuntu 9.04 with no issue and because i can run linux in console mode without issue. Thnx for the tip about the older livecd, ill check it out to see if that works. I'll post back after i try it out.

---

### Post by d_breidegam on 2009-05-02
ok, livecd of 8.10, 8.04 and 7.10 failed (i had disks already that i know work) so i figured i would check by removing ram and rebooting. I removed one of the new sticks and the error is gone. I replaced it and removed the other and again the error is gone. Replaced both and error returns. Does ubuntu not like 4gb of ram? slots are clean (cleaned them again just to be sure) and the ram works.

---

### Post by coffeecat on 2009-05-03
> **d_breidegam said:**
> I removed one of the new sticks and the error is gone. I replaced it and removed the other and again the error is gone. Replaced both and error returns.

Are they installed in dual-memory mode? And, if so, are they identical - i.e. same make, same model and a matched pair? If not, you're going to run into problems.

Also, freezing with even matched pairs can be a problem on some motherboards. I had this a couple of years ago with an otherwise perfectly good motherboard. I tried no less than three sets of matched pairs - different makes - all of which passed memtest individually, and I got random freezes with each pair. Used singly, all six sticks worked fine.

---

### Post by d_breidegam on 2009-05-03
yeah they were in dual memory mode and were same make and model. I ended up removing the 2 new sticks and using them for a different computer. Still, from a search around it seems as though problems are consistent for exactly 4gb of ram.

---

### Post by codeseer on 2009-05-03
> **d_breidegam said:**
> yeah they were in dual memory mode and were same make and model. I ended up removing the 2 new sticks and using them for a different computer. Still, from a search around it seems as though problems are consistent for exactly 4gb of ram.

I'm running 4 GB. Did you check for any motherboard firmware updates?

---

### Post by d_breidegam on 2009-05-06
firmware update fixed issue, thanks guys.

---

### Post by codeseer on 2009-05-06
> **d_breidegam said:**
> firmware update fixed issue, thanks guys.

Awesome! No problem. :P

---

