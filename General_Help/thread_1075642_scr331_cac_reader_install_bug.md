---
title: "scr331 cac reader install bug"
date: 2009-02-20
forum: General Help
---

### Post by djfick on 2009-02-20
I have a laptop and a desktop, both running Hardy heron.  I set up mt CAC reader on my laptop using the following info:

[http://ubuntuforums.org/showthread.php?t=564763&highlight=cac+reader](http://ubuntuforums.org/showthread.php?t=564763&highlight=cac+reader)

I tried to set it up on my desktop with the same how to, but when I insert my card, the pcsc scan says this:

Fri Feb 20 13:38:01 2009
 Reader 0: SCM SCR 331 (21120638230599) 00 00
  Card state: Card inserted, Unresponsive card,

The very same card is properly read when the reader is plugged into my laptop, but not on my desktop.  Does anyone with experience with these readers know why this may be happening?

---

### Post by cham93086 on 2010-03-01
Just had the same problem, I'm mucking around trying to get my CAC card working again-- it just went on the fritz, I suspect a bad update?(any ideas?)  Anyway, I cured it but un-installing and reinstalling pcscd and pcsc-tools, although I suspect restarting pcscd might have cured it?

---

