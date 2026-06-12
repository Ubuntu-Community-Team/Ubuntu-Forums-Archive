---
title: "Suspend no longer works after upgrade to 20.04.3"
date: 2022-01-18
forum: Desktop Environments
---

### Post by Gijsbert_Wiesenekk on 2022-01-18
Hi,

I upgraded Ubuntu on my laptop to 20.04.3 but suspend no longer works. Kernel version is linux-image-5.13.0-25-generic. Suspend also does not work with the previous version of the kernel linux-image-5.8.0-43-generic. Any workarounds?

Thanks,
GW

---

### Post by watchpocket on 2022-01-18
You might try installing a GA (General Availability) kernel (instead of an HWE (Hardware Enablement stack)) kernel (like 5.13.x and 5.11.x -- I'm not sure which of those 5.8.x is).

I believe the current GA kernel for 20.04 is *5.4.0-94-generic*.  That's what I'm using, but I use a desktop workstation, and I never suspend. 

I rolled back to 5.4.0 from 5.11.x because for me, USB audio didn't work in 5.11.

---

### Post by GhX6GZMB on 2022-01-18
20.04.1 is 5.4.0-xx, 20.04.2 and 20.04.3 are 5.8.0-xx

---

### Post by watchpocket on 2022-01-18
Hmm.  I am on 20.04.3, using 5.4.0-94-generic.  I may want to upgrade my kernel to 5.8.0-xx.
I am guessing 5.8.0 is a GA release.  Where might I go to learn more about 5.8.0 and its features?

I don't want kernel 5.11 - I already had it, and (at least for me) USB audio was not functioning in 5.11.

---

### Post by deadflowr on 2022-01-18
There is no more 5.8.
It was only supported during the 20.04.2 point release cycle.
Anyone who had that has since been upgraded to 5.11 and newer.
(Or they are running an out of date system)

> I am guessing 5.8.0 is a GA release
No, on 20.04 it was a HWE release.

---

### Post by watchpocket on 2022-01-18
Thank you. I will stick to kernel 5.4.0-94-*generic [Edit: 5.4.0-**96**-generic, see my next post]*  on 20.04.3 until late February when 20.04.4 is released with kernel 5.13.xx.

At that time, I'll keep 5.4.0-96 handy until I'm sure 5.13.xx is functioning well.

---

### Post by Gijsbert_Wiesenekk on 2022-01-18
HI,

I installed Zorin OS 16 for comparison. The kernel version is also linux-image-5.13.0-25-generic but now suspend works, so it is in some way related to the 20.04.3 build.

Regards,
GW

---

### Post by GhX6GZMB on 2022-01-18
> **watchpocket said:**
> Thank you. I will stick to kernel 5.4.0-94-generic on 20.04.3 until late February when 20.04.4 is released with kernel 5.13.xx.

At that time, I'll keep 5.4.0-94 handy until I'm sure 5.13.xx functions properly.
Very sensible strategy. I stay on 5.4.0-xx (at this time 94) myself.

---

### Post by watchpocket on 2022-01-18
Actually I just now upgraded to kernel ***5.4.0-96-generic***, which came in with today's updates, but I'm keeping -94 handy as a backup.  

I purge any kernels other than the current and the most recent release before the current.

---

### Post by GhX6GZMB on 2022-01-18
> **watchpocket said:**
> Actually I just now upgraded to kernel ***5.4.0-96-generic***, which came in with today's updates, but I'm keeping -94 handy as a backup.  

The system does this for you automatically.
Getting older versions is more tedious and normally unnecessary. I'm very happy with 5.4.0-94. Totally stable and with no issues at all.

---

### Post by watchpocket on 2022-01-18
Not sure what you mean by "older versions" -- 5.4.0-96 is newer than  -94, yes?

I just figure that if -96 pops up when I do *sudo apt update*, it's ok for me to update, as long as I keep the previous kernel installed.

So you go on the idea that there's some slight risk that -96 might introduce instabilities over -94?

And that if you know -94 is stable, the idea is to just leave it alone and don't move to -96?

---

