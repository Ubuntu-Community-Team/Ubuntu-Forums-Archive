---
title: "8-in-1 Media Card Reader on Vostro 1400"
date: 2008-03-10
forum: Dell  Ubuntu Support
---

### Post by King_Louie on 2008-03-10
I'm running hardy heron on a Vostro 1400. The media card reader is not recognized by the system. Does anyone else have a similar setup with a functional card reader? How did you get it going? Any tips on where I would look next to troubleshoot this? thanks.

---

### Post by notwen on 2008-03-10
I have had no problems w/ my card reader on my Inspiron 1420n, but there have been threads w/ Dellbuntu users having to enable their card readers in BIOS.  It may be possible that yours was also shipped disabled.  Check your BIOS settings and let me know if it was enabled there.  Hope this resolves your problems.  =]

---

### Post by King_Louie on 2008-03-10
The reader is enabled in the BIOS and works fine while booted into XP. It just doesn't show up in Ubuntu.

---

### Post by soapytheclown on 2008-03-20
ive identified the same problem on my 1700 it used to work on gutsy which is a pain :/

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

it is identified just not working :\

---

### Post by King_Louie on 2008-03-30
bump. 

anyone?

---

### Post by Phalco on 2008-05-14
Go to this post. It worked for me!

[http://ubuntuforums.org/showthread.php?t=760357](http://ubuntuforums.org/showthread.php?t=760357)

After install the package, I had to restart my system to get the reader works.

Hugs!

---

