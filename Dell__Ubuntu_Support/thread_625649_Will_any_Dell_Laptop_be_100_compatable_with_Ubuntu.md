---
title: "Will any Dell Laptop be 100 compatable with Ubuntu?"
date: 2007-11-28
forum: Dell  Ubuntu Support
---

### Post by JacobRogers on 2007-11-28
Will any Dell laptop be totally compatible with Ubuntu?

---

### Post by Dellfan on 2007-11-28
I think it depends on your definition of 100% compatible and the exact set of options on the specific notebook. 

For example, I would say my 1505 is 100% compatible, suspend/hibernate & resume work flawlessly, all the special keys work, the media buttons work, the DVD player works with commercial DVDs, it is able to burn CDs & DVDs. Of course, I had to tweak a few things but it really did come very close "out of the box". There seem to be some issues with the graphics card used on the 1420, and there certainly have been some teething issues with the Santa Rosa chipset.

If your question is will any notebook be 100% "out of the box" that is a different question and saddly the answer is likely no, due to licensing issues and really stupid laws in the US. I have heard rumors that Dell will be dealing with the commercial DVD issue, likely by licensing some player but have not seen anything yet. Perhaps when they officially start shipping 7.10.

---

### Post by jdelaros1 on 2007-11-28
It depends on the hardware on your Dell system. There are known issues with certain devices on Linux in general, some specific to Ubuntu. For example, there are issues with ATI video cards, as well as Broadcom wireless cards. Some video cards have issues with Suspend and Hibernate,

For the most part, Ubuntu 7.10 will recognize most of the hardware components on Dell laptops (or any other vendor) but you're likely to experience issues here and there.

For supported Dell hardware and known issues, see [http://linux.dell.com/wiki/index.php/Products/Consumer](http://linux.dell.com/wiki/index.php/Products/Consumer).

---

### Post by aysiu on 2007-11-28
I don't know about the new Dells, but my Dell Inspiron 500m laptop (before I gave it away) was 100% compatible with Ubuntu 7.04 and 7.10.

Suspend, multimedia keys, USB ports, sound, screen resolution... everything worked "out of the box." It didn't come with a wireless card when we originally purchased it, so I made sure to get a Linux-friendly wireless card (Intel Pro Wireless 2200).

---

### Post by Skuzniak on 2007-11-28
Very, very few machines will work right from the get-go with any form of linux, but I have had fantastic luck with my Vostro 1400 with Intel graphics. I had to do a workaround for compiz (un-blacklisting my card and changing video output so I could retain video playback ability), ndiswrapper for the wireless card and rebuild alsa from source to get sound working. Takes less than 10 minutes to do the steps I mentioned, then everything (suspend/hibernate/resume/wifi/sound/resolution/compiz/ect) works perfectly.

---

### Post by ubutufan on 2007-11-28
What machine do you use mate?

---

