---
title: "Dual OSes - two drives"
date: 2008-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stevecoh1 on 2008-09-14
I bought this Inspiron 530 computer earlier this year from Dell.  I previously used RedHat and thought I could just mount my existing drive (which was working) and transfer all my stuff over.  Alas, RedHat was incompatible with the 530, so I did a little research and found that if I had been a little smarter I could have bought the computer from Dell with Ubuntu installed.  Oh well, I just bought another hard drive, put Ubuntu 7.10 on it and have been a happy camper ever since.

Well, almost.  I have the occasional use for Windows, so I decided to keep the original hard drive intact and mount both in the box and just boot to Windows when I need to which is infrequent.  I also decided not to mess with Grub or LILO and just rely on the CMOS startup to switch between them.  There is a boot utility that lets me pick.  

Alas, it doesn't work reliably.  I find that on restarting the computer (which is set to boot off the Ubuntu disk), it only succeeds about 20% of the time.  The other 80% of the time, the Ubuntu progress meter appears and never makes it beyond the first bar.  I have to retry, turn the computer off and on repeatedly to get the thing to boot.  Once it boots, it's fine.

Now I've gone and purchased an IPhone.  Since there is no ITunes support for this, my need to boot Windows is more frequent than it was before, and I would like to get this resolved.

So my choices are 
1) finding something to do with my boot configuration to make it more reliable.
2) incorporating my Windows disk into the Grub system and using Grub as the switch between the two OSes.  I had been hoping to avoid this, so as to keep the existing Windows disk in factory configuration, but if that will solve my problem, I'm willing to make that change.

Can anyone suggest why this problem occurs?  Is it because there are two bootable drives in my machine.  If so, why do I never have this problem when I choose to boot from the Windows disk, but only from the Ubuntu disk?

Thanks in advance for any help.

---

### Post by stevecoh1 on 2008-09-14
further information:

I have found that placing the Ubuntu 7.1 CDROM in the CDROM drive and rebooting, and then selecting "boot from first hard drive" works reliably in this hardware configuration, but leaving the CDROM out and letting it go direct to the hard drive fails more often than it succeeds.

Why should this be?

---

