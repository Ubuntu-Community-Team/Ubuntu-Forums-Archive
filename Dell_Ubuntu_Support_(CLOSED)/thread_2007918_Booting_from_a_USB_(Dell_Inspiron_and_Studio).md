---
title: "Booting from a USB (Dell Inspiron and Studio)"
date: 2012-06-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rukita on 2012-06-21
I'm having significant booting issues on my Dell Studio 1558 (Windows 7) which I believe is due to a failing hard drive (or software issues making the hard drive invisible to the rest of the computer).  [I found an article outlining how to boot Ubuntu from a CD and access your hard drive that way.]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") []("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")

I opted to create a USB stick instead of a CD, following the instructions [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows").
I created the USB using my other laptop, a Dell Inspiron e1705 (Windows XP).  I then tried loading from the USB in the Inspiron; it was a bit slow but definitely worked.

I then tried loading from the USB in my other, non-functioning computer.  It never loaded; the text on the screen reads:

status: { DRDY ERR }
error: { ABRT }
qc timeout (cmd 0xec)
failed to IDENTIFY (I/O error, err_mask=0x5)" "revalidation failed (errno=-5)
hard resetting link
SATA link up 3.0 Gbps (SStatus 123 SControl 300)
configured for UDMA/100 (device error ignored)
EH complete
exception Emask 0x0 SAct 0x0 action 0x0
irq_stat 0x40000001
failed command: read dma
cmd c8/00:00:08:00:00..... <-- continues, don't want to type the whole line out
res 51/04:08:00:00..... <--- also continues

and it just loops like that ad infinum.

Is it possible that it's not booting because I created the bootable USB on my Inspiron (different model than the Studio, Windows XP instead of 7)?  Or is the problem that the Studio is in worse shape than I thought?

Any insight would be appreciated.

---

### Post by wilee-nilee on 2012-06-21
Make sure you load the usb with a loader such as unetbootin.

Use the per-session boot, on my dell it is f12 at powering as if you were going to the bios. This is a out of the bios boot from menu.

The key or keys to this menu may vary with model or manufacturer as well.

---

### Post by Rukita on 2012-06-21
> **wilee-nilee said:**
> Make sure you load the usb with a loader such as unetbootin.

Use the per-session boot, on my dell it is f12 at powering as if you were going to the bios. This is a out of the bios boot from menu.

The key or keys to this menu may vary with model or manufacturer as well.

I used Pen Drive Linux as per the instructions... was that what you were referring to by a "loader"?

I used the F12 booting method and selected "USB Storage" (it had a + next to the text, so clearly it recognized something was there.

I was able to get as far was the first Ubuntu window that asks what you want to do.  I selected "run Ubuntu from USB" (can't remember exact text), and it starts to load and then gets stuck and starts printing the text/error messages (see above) over and over again.

---

### Post by critin on 2012-06-21
> Is it possible that it's not booting because I created the bootable USB  on my Inspiron (different model than the Studio, Windows XP instead of  7)?  Or is the problem that the Studio is in worse shape than I thought?No, that makes no difference.  I always have better luck with unetbooting than with Universal.  That's only my experience though.

I've had the same  **{ DRDY ERR }   **on a faulty HD.  (Many faulty sectors)  I'm still using the HD though.  I would copy the files again in the flash and use TRY, once you get on the desktop you can look at the disk with disk utility to see if it is failing, and install from desktop if you choose to.

My Dell identifies the boot flash as 'flash', not 'storage'.

---

### Post by C.S.Cameron on 2012-06-21
Yeah, try UNetbootin or Startup Disk Creator.
Startup Disk Creator is on the Live CD.

---

### Post by mscout2004 on 2012-06-21
I agree with critin it sounds like your HDD is showing signs of going bad. I had the same problem when my HDD was going out and I tried to install Ubuntu.

---

### Post by Lee_Bo on 2012-06-22
What brand and size of USB drive did you use?  I'm finding that some brand/size combos are not as reliable as others.  PNY 8 gig, for me at least, seems to be a sweet combination with Ubuntu.

---

