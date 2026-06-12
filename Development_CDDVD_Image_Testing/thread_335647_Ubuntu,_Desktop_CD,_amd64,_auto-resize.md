---
title: "Ubuntu, Desktop CD, amd64, auto-resize"
date: 2007-01-10
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-01-10
Test case type: **Ubuntu, Desktop CD, amd64, auto-resize**
Image ID: **20070110**
Date of testing: 2007-01-10
md5sum confirmed: **Yes**
Pass/Fail: [COLOR=Red]**FAIL**[/COLOR]
Bugs identified: **[#78722]("https://launchpad.net/bugs/78722")** -- Grub ignores previous install
Other comments:

---

### Post by davmor2 on 2007-01-11
Test case type: Ubuntu, Desktop CD, amd64, auto-resize
Image ID: 20070110
Date of testing: 2007-01-10
md5sum confirmed: Yes
Pass/Fail: FAIL
Bugs identified: #78722 -- Grub ignores previous install
Other comments:  Once the cd is ejected you are told to press "enter" when I do nothing happens.  This is both after a live session or an install.

---

### Post by Hershey on 2007-01-14
Test case type: Ubuntu, Desktop CD, amd64, auto-resize
Image ID: 20070110
Date of testing: 2007-01-14
md5sum confirmed: Yes
Pass/Fail: FAIL
Bugs identified: #67545
Other comments: 

Once the cd is ejected you are told to press "enter" when I do nothing happens. 

Xorg was using vesa driver instead of nv.

Install screen said 7.04 was coming out April 2006.

Clicking on next during install didn't always work.  Need to click some where else on the screen, then clicking on next would work.

---

### Post by chalex on 2007-01-15
Once the cd is ejected you are told to press "enter" when I do nothing happens.

I can confirm this problem on two different amd64 test machines.

---

### Post by Henrik on 2007-01-15
> **chalex said:**
> Once the cd is ejected you are told to press "enter" when I do nothing happens.


... and I remember seeing a bug about this, but I can't find it now. Perhaps it's been marked Fixed?

---

### Post by pochu on 2007-01-15
Yes, here is the bug (and it's unconfirmed):
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/68054](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/68054)

Add a comment confirming it if you have it.

Regards
Pochu

---

