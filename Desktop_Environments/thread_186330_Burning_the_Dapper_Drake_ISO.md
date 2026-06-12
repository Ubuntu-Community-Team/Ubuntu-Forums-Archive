---
title: "Burning the Dapper Drake ISO"
date: 2006-06-01
forum: Desktop Environments
---

### Post by sardopsycho on 2006-06-01
Question...

I ran out of blank CDs and all I have are DVDs....

Can I burn this ISO onto a DVD+R - and it actually work???

thanks!

---

### Post by Rackerz on 2006-06-01
Yep, I burned my CD ISO to a DVD using Nero :).

---

### Post by arsolto on 2006-06-01
As to record an archive of image (ISO) in a COMPACT DISC. 

Some applicatory appearances to facilitate a daily work of writing of CDs exist, but to the times it is more interesting to use the command line, either to automatize one procecsso or to demand less of the machine. For this then it uses the CDRECORD.

If you are using a flexible media (CD-RW) that already she has some content erases it first:

**$ cdrecord -v dev=/dev/??? blank=fast speed=X**

And to record the image in the CD:

**$ cdrecord -v dev=/dev/??? speed=X -data debian-br-cdd_1.0.iso**

It changes:        

*??? (for hdc (or the alternative way of its device) or what it will be found in the line of the CD-R when executing "$ cdrecord -scanbus").

*X (for the speed of the recorder, respecting the supported one for the media).

---

