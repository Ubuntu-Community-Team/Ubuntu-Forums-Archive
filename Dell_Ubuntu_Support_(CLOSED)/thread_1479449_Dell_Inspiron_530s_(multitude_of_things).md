---
title: "Dell Inspiron 530s (multitude of things)"
date: 2010-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tzar Meathammer on 2010-05-10
Thanks for checking.
1: I put Ubuntu onto my external hard drive, but now I can't load my windows on my normal Hard Drive. I might of accidentally partitioned it, but I didn't do anything with it. All it says is 
"GRUB loading
error: no such disk
grub rescue>"

2: I can't get a driver for my Intel Family Chipset G33/G31 to work.

3: I love you. That wasn't really needed but you people are always so helpful.

---

### Post by gbrainin on 2010-05-10
Most likely the install of Ubuntu overwrote the MBR on your primary hard drive.  If you have the external hard drive connected, GRUB should be able to load (it probably stored its files there), and you will probably find Windows as one of the selections on the GRUB menu.

Or you could just restore the MBR of the Windows drive.  Precisely how to do that will depend on what version of Windows you're using, but a search on the appropriate version and "restore mbr" should find you instructions.

Or you could try this: [http://ubuntuforums.org/showthread.php?t=622828]("http://ubuntuforums.org/showthread.php?t=622828")

---

### Post by gbrainin on 2010-05-10
P.S. If you actually repartitioned your primary drive, fixing it will be a bit trickier.  Here again, your Ubuntu live CD can help.  Search on "restore lost partition."  Expect to do some reading before you try anything.

---

