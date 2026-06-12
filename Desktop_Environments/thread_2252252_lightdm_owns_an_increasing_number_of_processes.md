---
title: "lightdm owns an increasing number of processes"
date: 2014-11-10
forum: Desktop Environments
---

### Post by zeke2135 on 2014-11-10
I am noticing that lightdm is shown as owning an increasing number of copies of processes, including init, indicator-sound-service, etc. See attached screen shot. The processes seem to increase when I switch between users logged in to different sessions. 

I also see a gradually increasing memory usage (in the used column of the -/+  buffers/caches line of free), but the memory usage (e.g. going from ~1.2GB for two users up to ~2GB roughly a day or two after a reboot) is quite a bit more than would be accounted for by the extra processes.

I've seen this on two machines, almost identical hardware but different graphics hardware (nvidia GT630 and radeon 6450). They have Asus A88XM-A motherboards. 

I am running ubuntu 14.04.1 w/ the most recent updates. 

Any hints would be welcome.

---

