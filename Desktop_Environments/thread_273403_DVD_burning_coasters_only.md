---
title: "DVD burning coasters only"
date: 2006-10-08
forum: Desktop Environments
---

### Post by jerryjvl on 2006-10-08
Last time I burned a DVD successfully was 2-3 months ago, with the same hardware and software:
- Pioneer DVR-110D, firmware: 1.41 (latest!)
- K3B (and GnomeBaker, and growisofs directly from the command-line)

Invariably, the burning fails in growisofs along the lines of (from the K3B log):
growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 16.4x1385KBps.
  19562496/4396314624 ( 0.4%) @2.9x, remaining 22:22 RBU 100.0%
  34406400/4396314624 ( 0.8%) @3.1x, remaining 19:00 RBU 100.0%
  42336256/4396314624 ( 1.0%) @1.7x, remaining 22:16 RBU 100.0%
:-[ WRITE@LBA=50c0h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument


I have already re-installed everything in the tool-chain, and even updated to the latest available version of growisofs (6.1).

Nothing seems to stop this error from occurring, and it is growing to be a big problem because my data archives need to be purged... soon.

Does anyone have any suggestions what might be causing the issue, or approaches that might fix it?

PS: Note that the percentage it reaches before failing varies wildly; sometimes I get to 20%, or even 60%. I have tried burning different lists of files, but they all eventually fail.

PPS; I have had *some* limited success in burning after a re-boot, but only for one disc. After a succesful burn the next (and every following) disc fails in this fashion. I cannot however keep rebooting my machine to get good burns.

---

### Post by jerryjvl on 2006-10-08
Anyone at all? ...

---

### Post by wpshooter on 2006-10-08
Have you tried simply cleaning the drive ?

Personally, I think I would get rid of those other two programs and stick with strictly K3b.  

I would recommend using rewriteable media, so you don't wind up wasting CDs.  

Get yourself some good quality CD-RW medias.

---

### Post by jerryjvl on 2006-10-08
> **wpshooter said:**
> Have you tried simply cleaning the drive ?
No; how would I go about that? What needs cleaning?

> **wpshooter said:**
> Personally, I think I would get rid of those other two programs and stick with strictly K3b.
I normally only use K3b... was only using the others to see if it was something app-specific.

> **wpshooter said:**
> I would recommend using rewriteable media, so you don't wind up wasting CDs.
Although I'll continue using DVD-R's for my actual burns, it's a really good suggestion to use a DVD-RW while I try to figure out what is wrong... thanks for that.

---

