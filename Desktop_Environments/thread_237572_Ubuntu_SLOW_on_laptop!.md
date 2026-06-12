---
title: "Ubuntu *SLOW* on laptop!"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Yv12345vY on 2006-08-16
Hello,

I installed the latest version of Ubuntu on a Centrino-based Alienware laptop.  It's SLOW!  It takes forever to boot.  Opening up Mozilla takes a good two minutes!!!

CPU is usually maxed out but top/gnome-panel both show those utilities taking up most CPU time.  The hard drive spins almost all the time.

I re-built the kernel disabling SMP and specifying Pentium M as processor type with no luck.

Help!!

---

### Post by DoctorMO on 2006-08-16
Try Xbuntu, it's got a smaller memory footprint.

You might like to post your specifications for your machine so we can mull over the posibilities.

---

### Post by Yv12345vY on 2006-08-16
> **DoctorMO said:**
> You might like to post your specifications for your machine so we can mull over the posibilities.

Gladly:

Pentium M 1.6
1gb ram
60gb 7200 rpm HDD
Intel 855 video

---

### Post by patrickfromspain on 2006-08-16
there's obviously something wrong... I use a Toshiba laptop with the celeron M processor and intel 852 video and it isn't that slow... look into /var/log to see if one of the files helps debbuing the problem.

Anyway.. it's not the first message with alienware causing problems :(

---

### Post by Yv12345vY on 2006-08-16
> **patrickfromspain said:**
> there's obviously something wrong... I use a Toshiba laptop with the celeron M processor and intel 852 video and it isn't that slow... look into /var/log to see if one of the files helps debbuing the problem.

Anyway.. it's not the first message with alienware causing problems :(

Yeah, I have looked into the logs a little but it's just so damn slow I get discouraged quickly.  I'll definitely post anything interesting I find.

---

### Post by Yv12345vY on 2006-08-18
I found something on SuSe support forums saying that support for large amounts of RAM is lacking and a few people said that cutting ram to 512 (or specifying to the kernel at boot time to use 512) made SuSe run smooth.  Did anybody run into something similar with Ubuntu?

---

### Post by Yv12345vY on 2007-11-02
This is long overdue but adding "mem=512M" or "mem=768M" to boot parameters solved this problem!

---

