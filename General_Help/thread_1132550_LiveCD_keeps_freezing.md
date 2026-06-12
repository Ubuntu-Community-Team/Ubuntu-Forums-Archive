---
title: "LiveCD keeps freezing"
date: 2009-04-22
forum: General Help
---

### Post by 2quick on 2009-04-22
Hello!  I am having an issue trying to get Ubuntu to install properly.  I am installing the 64 bit on my Asus laptop that has a Intel processor on it and currently running Vista 64 bit.  When I run the LiveCD it keeps freezing when I try to open up Gparted or any other application.  Sometimes it will work, then freeze up.  Sometimes I will click on something and the wait pointer appears then disappears and nothing opens up.  Does anyone know what could be causing this issue.  I tried burning a new copy of the disc and also trying the 32 bit version with the same issues.

Additional note, when I just tried to start the LiveCD Gparted started to run, then froze.  I could push the shutdown button and when I did the screen starting rolling an error that the only part you can read is SQUASHFS.

Thanks!

---

### Post by s.fox on 2009-04-22
Hi,

That sounds like an odd problem.

Have you tried running CD integrity check?  On the options menu when running the CD you should see the following "Check CD for Defects".

It might also be worth verifying data integrity using the MD5 128-bit cryptographic hash.   Information on how to perform this check can be found [here]("https://www.help.ubuntu.com/community/HowToMD5SUM").

Hope this helps.

-Ash R

---

### Post by 2quick on 2009-04-22
Hi, thanks for the reply. 

Unfortunately I had checked the ISO image and a data check on the cd prior to doing anything. 

Any other ideas?

Thanks!

---

### Post by chomptown on 2009-04-22
Did you burn the disk at a nice low speed?  Even if you checked the ISO md5 checksum, and checked the disk prior to writing, there could have been an error when you burned the disk.

---

### Post by Godly on 2009-04-22
Burn again at slower speed. I had the same issue.

---

### Post by 2quick on 2009-04-22
I had also done the data check when I first inserted the disk. 

I burned the disk at 8x. Think that was too fast?

Thanks!

---

