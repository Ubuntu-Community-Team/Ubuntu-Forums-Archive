---
title: "VMWare Player -&gt; kernel panic &amp; hang"
date: 2006-01-11
forum: Desktop Environments
---

### Post by datajack on 2006-01-11
Hi,

I am trying to get VMWare player to work on my Dell 'Precision Workstation M50' laptop and am running into problems.

I am running kernel 2.6.12-10-686 so I nhave had to compile the vmmon module. This appears to be sucessful after installing gcc-3.4 However, the system invariably hangs solid shortly after the module is inserted into the kernel. I have managed once to flip to the text console at the right time and saw a kernel panic message appear on screen, but neglected to copy down the details of the end of this report (all I could see by this point was the tail end of the register dump and backtrace). I have also tried this with the 386 class kernel with the same results.

Is anyone else having this problem? Can anyone have a guess at how to fix it, or is there an easy solution I've missed?

Failing all that, is there a good LKCD howto for Ubuntu?

Any help would be greatly appreciated.

---

### Post by bikeboy on 2006-01-19
Same kernel, almost same problem. When I run it from the terminal it tells me that VMware Player is not correctly configured for my system, despite me doing that numerous times. It did work initially but since then, nothing....

---

