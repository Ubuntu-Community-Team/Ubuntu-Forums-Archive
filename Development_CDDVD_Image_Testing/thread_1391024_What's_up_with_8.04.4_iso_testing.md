---
title: "What's up with 8.04.4 iso testing?"
date: 2010-01-26
forum: Development CD/DVD Image Testing
---

### Post by kansasnoob on 2010-01-26
I even received an email the morning of the 21st:

> You are receiving this email because you have been subscribed to the
following test case:

Ubuntu Desktop i386 [20100121.1]: [http://iso.qa.ubuntu.com/qatracker/info/3590](http://iso.qa.ubuntu.com/qatracker/info/3590)
Install (auto-resize): [http://iso.qa.ubuntu.com/qatracker/result/3590/9](http://iso.qa.ubuntu.com/qatracker/result/3590/9)
Install (entire disk): [http://iso.qa.ubuntu.com/qatracker/result/3590/5](http://iso.qa.ubuntu.com/qatracker/result/3590/5)
Install (manual partitioning): [http://iso.qa.ubuntu.com/qatracker/result/3590/7](http://iso.qa.ubuntu.com/qatracker/result/3590/7)
Live Session: [http://iso.qa.ubuntu.com/qatracker/result/3590/3](http://iso.qa.ubuntu.com/qatracker/result/3590/3)

Please report any bugs you identify in Launchpad and report on the
success or failure of the test in the tracker:
[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)

Please see the testing team wiki pages for for further information:
[https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

For questions about the procedure or to coordinate testing, please join
#ubuntu-testing on freenode.

Thank you for helping us to test Ubuntu.


But even then the link says, "This build wasn't found on [http://cdimage.ubuntu.com/daily-live/20100121.1/hardy.4-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/20100121.1/hardy.4-desktop-i386.iso) (may no longer exists)".

So I've even googled and found nothing :)

But the iso does exist:

[http://cdimage.ubuntu.com/hardy/daily-live/current/?C=S;O=D](http://cdimage.ubuntu.com/hardy/daily-live/current/?C=S;O=D)

And I found this:

[http://ubuntutesting.wordpress.com/](http://ubuntutesting.wordpress.com/)

---

### Post by Puck7 on 2010-01-26
It's fairly easy, the QA team sent out the testings, they agreed on the mailing list to do so. From now on who is subscribed to the requests, or did subscribe before, will get a notice through email that their services are needed.

Probably you can get an image from [http://cdimage.ubuntu.com/hardy/daily-live/current/](http://cdimage.ubuntu.com/hardy/daily-live/current/) - These seem updated.

---

### Post by kansasnoob on 2010-01-26
> **Puck7 said:**
> It's fairly easy, the QA team sent out the testings, they agreed on the mailing list to do so. From now on who is subscribed to the requests, or did subscribe before, will get a notice through email that their services are needed.

Probably you can get an image from [http://cdimage.ubuntu.com/hardy/daily-live/current/](http://cdimage.ubuntu.com/hardy/daily-live/current/) - These seem updated.

But the links led to an invalid download! I've now tested and found all installations end in a kernel panic.

I'm sure the devs can get that fixed in just a few hours :mad:

---

