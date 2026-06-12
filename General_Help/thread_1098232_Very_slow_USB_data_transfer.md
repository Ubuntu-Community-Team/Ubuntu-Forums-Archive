---
title: "Very slow USB data transfer"
date: 2009-03-16
forum: General Help
---

### Post by aczar on 2009-03-16
Hi

I've had this same problem with my desktop and laptop. If I try to transfer data from an external USB (2.0) hard drive or USB key, it starts out fast and then quickly drops down to about 1 MB/sec. I've looked around a bit and found that others have had similar problems, but I haven't found any solutions. Any suggestions will be greatly appreciated.

thanks
alex

---

### Post by kuja on 2009-03-17
1MB/s is the speed of USB 1.1. Try a different USB port/hub and see if the problem remains the same. Also take a look at /var/log/dmesg and see if it says anything about it.

---

### Post by ruel- on 2009-03-17
is it a USB 2.0 port?

---

### Post by aczar on 2009-03-17
Yeah, I checked that before I posted. It is a USB 2.0 port. And, as much as it pains me to say it, the transfer is fast as expected in windows.

---

### Post by ruel- on 2009-03-17
how about your USB device, is it 2.0? I have a USB ZIP 1.0 and it has slow data transfer just like what you are saying..

---

### Post by aeiah on 2009-03-17
what version of ubuntu are you using? i have the same problem but im using 7.10. my girlfriend has no problems with 8.04, although that may be down to her intel motherboard and the fact that it seems to be the most linux compatible desktop machine ive ever seen.

perhaps upgrading will help, although obviously be careful not to bork your system. kernel upgrades will knock out compiled driver modules and such but you can always roll-back in grub.

---

### Post by aczar on 2009-03-17
yep. also 2.0. It starts out at 2.0 speeds, but then gradually slows down to a crawl over 30 sec or so. With very big transfers it continues to slow down, I tried backing up about 9 gigs yesterday and by the time it got half way through it was going at about 500 kB/s

---

### Post by aczar on 2009-03-17
> **aeiah said:**
> what version of ubuntu are you using? i have the same problem but im using 7.10. my girlfriend has no problems with 8.04, although that may be down to her intel motherboard and the fact that it seems to be the most linux compatible desktop machine ive ever seen.

perhaps upgrading will help, although obviously be careful not to bork your system. kernel upgrades will knock out compiled driver modules and such but you can always roll-back in grub.

using 8.10

---

### Post by ROOP on 2009-03-17
Currently having the same problem using Ubuntu 8.10. Extremely slow USB transfers. It worked fine not to long ago. Speeds were as they should be, but now around 1000 kb/s. Compared to 25 MB/s. Don't know what went wrong.

---

### Post by lisati on 2009-03-17
I'm wondering if there's some kind of tweak to buffer and/or cache settings that might help.

---

### Post by aczar on 2009-03-24
bump

---

### Post by neodaemon on 2009-03-31
I'm also having the same problem. I read this entire thread:
[http://ubuntuforums.org/showthread.php?t=793688](http://ubuntuforums.org/showthread.php?t=793688)
...and it seems to be the root cause - at least for me. I checked the referenced bug reports and the bugs are still unresolved after more than a year.

It is quite frustrating as USB storage is pretty important.

Forgot specs:
Ubuntu, fresh install of 8.10 with only the latest Ubuntu updates.
USB 2.0 verified ports and flash drive.
Less than 1 MB/sec transfers from internal SATA drive to USB flash drive.
Lightening fast transfers between internal drives.

---

### Post by aczar on 2009-03-31
Thanks for the link. Just read through it too. 

If I could close this thread I would, no sense in repeating everything. Mod?

---

