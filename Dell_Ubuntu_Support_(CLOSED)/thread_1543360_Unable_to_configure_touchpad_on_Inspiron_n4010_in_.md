---
title: "Unable to configure touchpad on Inspiron n4010 in Lucid lynx"
date: 2010-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by a2l007 on 2010-07-31
Hi all, I recently bought a dell inspiron n4010 and installed lucid lynx. The problem is that my touchpad driver is not configured, ie i'm not able to do any vertical or horizontal scrolling.My touchpad also supports rotate and zoom in facilities,but i'm unable to use in Linux. I tried installing gsynaptics, but they've asked me to set SHMConfig to true in xorg. But Lucid doesnt have xorg AFAIK :(
Please help me out..Am i proceeding in the right direction?



Thanks in advance..

---

### Post by mandol on 2010-08-01
I own the same model, and I haven't been able to configure the touchpad either.

I'm on Kubuntu Lucid.

I've only found one [thread]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/551234") with anything to do on the subject. The thread fixes a minor issue, but the overall issue of configuring the touchpad is still not dealt with in any thread (of all the ones that I've gone through so far at least)

I installed gsynaptics and I get the "Set SHMConfig to True in xorg.conf" message too

Any help would be appreciated.

Regards,

Kartik Krishnan

---

### Post by a2l007 on 2010-08-04
Can anyone help out?? Would i have to wait till Maverick Meerkat to get this issue resolved?:-?

---

### Post by brkearns on 2010-09-28
I am in the same boat.  Interesting thing is the troubleshooting file in the synaptics driver doc that clearly states "If it is identified as a "PS/2 Generic Mouse" or "PS/2 Synaptics TouchPad", something is wrong."
 
Well, something is wrong because that is what the kernel says my touchpad in this Inspiron N4010 is.  I wonder if it is some black market knock-off or if Synaptics really intentionally changed this property in the firmware.

Inquiring minds want to know.....

---

### Post by brkearns on 2010-10-01
Synaptic Touchpads on the Inspiron N4010 work well with 10.10 (Linux kernel 2.6.35-22-generic).:KS

---

### Post by rafe.kettler on 2010-10-14
> Synaptic Touchpads on the Inspiron N4010 work well with 10.10 (Linux kernel 2.6.35-22-generic).:KS

Mine works fine with Maverick for one finger. If I put two fingers on it, the cursor spazzes out and moves all over the place.

I don't really care though, because I usually use a mouse and I'm pretty used to just using the far right side of the touchpad for vertical scrolling.

---

