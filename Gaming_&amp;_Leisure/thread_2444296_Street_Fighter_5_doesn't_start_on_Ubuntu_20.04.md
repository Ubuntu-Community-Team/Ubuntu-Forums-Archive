---
title: "Street Fighter 5 doesn't start on Ubuntu 20.04"
date: 2020-05-28
forum: Gaming &amp; Leisure
---

### Post by drscosta on 2020-05-28
Hi everyone,

I've switched to Ubuntu 20.04 recenly and I've been loving the OS so far, and then I've read that Street Fighter 5 was finally perfectly playable on proton 5.0.7.

Thing is, it doesn't really work for me.

Every time I start the game this happens:

[IMG]https://i.ibb.co/1n8fWxc/Screenshot-from-2020-05-28-09-27-19.png[/IMG]
[https://ibb.co/1n8fWxc](https://ibb.co/1n8fWxc)

My bet is that my graphics card (AMD R9 290x) is working with the **radeon** driver instead of **amdgpu** and therefore can't start **vulkan,** but I could be far off.

Can anyone help me sort this?

my specs:

AMD FX 8320
Saphire Radeon R9 290x Vapor-x
16gb RAM ddr3 1600mhz
120GB SSD (root mounted here)
1TB 7200rpm HD
250gb 5400rpm HD for backups

---

### Post by drscosta on 2020-05-28
Managed to get it working, the issue was indeed the driver.

I had to install the oibaf drivers and blacklist the radeon driver in modprobe.d

If anyone has the same issue in any other game, with similar hardware (from my research, this commonly happens in r9 200 and 300 series), I'll gladly help!

---

