---
title: "Dualbooting xp/Ubuntu on Mini 9"
date: 2009-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaqrah on 2009-02-27
Is anybody out there dualbooting Xp/Ubuntu on their Mini 9? 

Yes? No?  Does anybody have any opinions on the matter, pros and cons?

Interested in ideas and opinions.

I have 32g ssd, enough room for 2 os.

---

### Post by notwen on 2009-02-27
I'm dual-booting my Mini 9 on a 16GB SSD.  I use a 16GB SDHC card for storage for both XP and Ubuntu.  I would recommend using the ext2 file system for Ubuntu if you're concerned w/ the read/write limitations of SSDs.  Also the particular version of XP i'm running I found at Micro Center is for **U**ltra **L**ow-Cost **PC**s(ULPCs).

---

### Post by armandh on 2009-02-27
I dual booting XP and 8.10

create an active primary NTSF partition of the desired size
install the xp first. it will install to the active primary partition. then install the ubuntu NOT THE DELL UBUNTU and select guided use largest unpartitioned space. ubuntu will create and install to an extended partition in the remaining space.

I found NO way to use the dell 8.04 and xp.
the dell dvd wipes the drive, creates and copies the 8.04 OS to a primary active partition [using the whole drive.]

xp does not play well with another primary active OS in front of it.

---

### Post by jaqrah on 2009-02-28
Thanks for the replies.

Notwen-How is the SDHC card working for memory?  I have yet to buy one for my Mini.  I have been using a USB drive, but I would like to have options.

Armandh-I am already dual booting on my desktop, so I have that aspect down.  


Have either of you felt any limitations or issues when dual booting.  And which version of Xp are you running?  Home, Pro, MC?  I didn't see the ULPC version on the Micro site.

---

### Post by notwen on 2009-02-28
> **jaqrah said:**
> Thanks for the replies.

Notwen-How is the SDHC card working for memory?  I have yet to buy one for my Mini.  I have been using a USB drive, but I would like to have options.

Have either of you felt any limitations or issues when dual booting.  And which version of Xp are you running?  Home, Pro, MC?  I didn't see the ULPC version on the Micro site.

In Ubuntu I have it mounted to under /media and in XP it's just picked up as an additional drive.  This version of XP is XP Home for ULPCs.

---

### Post by armandh on 2009-02-28
XP professional/SR2: the dell driver disk that comes with the mini9 is quite handy.

8.10 with compiz cube running is no strain for the video
medibuntu.org options loaded and it will play DVDs [external drive]

---

