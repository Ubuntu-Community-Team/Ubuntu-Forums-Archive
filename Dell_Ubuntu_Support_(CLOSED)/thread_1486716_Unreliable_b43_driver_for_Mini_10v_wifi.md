---
title: "Unreliable b43 driver for Mini 10v wifi"
date: 2010-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rcorai on 2010-05-15
Hi,
I have BCM4322 wifi card and I can connect to Internet but the connection is too slow and sometimes I lost the connection.
It was working fine on Ubuntu 9.x but not with this 10.04 version.
Can you help me to fix this issue?
Thanks,

---

### Post by chicken159 on 2010-05-16
I have had this same issue ever since I went to 10.04 at Alpha 2 - the STA driver is slow and hangs repeatedly, the B43 driver doesn't work at all. I've so far found a number of people reporting the same issue, but all the bug reports/solutions seem to ignore the issue with the STA driver since it 'works' - ie. it can be installed and connects. The fact that its slow, and often useless doesn't seem to have been addressed at all. 

This is still a huge issue, with no solution - anyone know what is happening here?

---

### Post by Matt__ on 2010-05-16
I had these problems on my mini 10v too.

[See thread here]("http://ubuntuforums.org/showthread.php?t=1474612")

since then I took off netbook 10.04 version and installed the standard desktop 10.04.
It suffered NONE of the wireless woes of netbook, once I had updated and installed the STA driver it identified 10 local networks (more than ive ever seen before at home) and connected instantly with good range.

Not found any disadvantages to using desktop version yet. made the most of screen res by making folder/app headings 6pt font in appearance/font/window title and auto hiding panels.

---

### Post by chicken159 on 2010-05-18
I have the desktop version on my 10v, and still have the hanging/unreliable connection with the STA driver (b43 incompatible).

I have now taken to carrying my USB dongle with me - is this not considered a serious problem?

---

### Post by Linoobius on 2010-05-18
I'm having the same issue on a Dell Latitude E5500 running Lucid Lynx 10.04 Desktop version. It has the BCM4322 chipset and the wireless connects fine but the connection only works in short bursts. I can boot back into 9.10 and the problem disappears. I have tried removing and reinstalling the STA driver as well as downloading the latest linux driver from Broadcom and compiling and installing it on my system and get the same results. Connectivity is almost useless. I hope someone finds a solution to this soon as wireless is my only option at the office.

---

### Post by STLGentleman on 2010-06-05
just wanted to bump this thread as I'm having the same exact problem as others. I'm using the b43xx driver and my wireless works in short bursts. This was never a problem in previous ubuntu releases.

Hopefully this can be resolved soon and not something we'll have to wait for in the next release.

I switched from network-manager to wicd in hopes that would change things but it didn't. 

= / H E L P

---

### Post by tdl720 on 2010-06-14
I've also had luck with neither the B43 driver nor the STA driver.  I think I may have to revert  to an earlier release.

---

### Post by tdl720 on 2010-06-15
After a clean reinstall of Lucid, I activated B43, deactivated B43, activated STA, deactivated STA, reactivated STA, and found that my wireless interface works fine.  I don't know what it took, but the STA driver does seem to eventually work with lucid for the Dell mini 10v.

---

### Post by caseygibbs on 2010-09-12
Bump. Feel like I've tried everything. Worked well in previous versions til I updated (ordinary updates, not distro upgrades), then toasted. Tried wicd to no avail. Considering moving to a different distro. It's maddening.
--Coincidentally, but not that humorously or unexpectedly, I lost my signal while writing this post.

---

