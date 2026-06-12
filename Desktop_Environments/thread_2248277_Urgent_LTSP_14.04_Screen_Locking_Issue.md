---
title: "Urgent LTSP 14.04 Screen Locking Issue"
date: 2014-10-13
forum: Desktop Environments
---

### Post by pat-rynoceris on 2014-10-13
Hello all!

Firstly, I'm not sure where to put this post, so I hope I got it (somewhat) right. I very recently moved a doctors office using Windows Server 2008 over to a diskless thin-client environment using LTSP on an Ubuntu 14.04 VM as a passthrough. One of the original developers of LTSP had to assist with this integration, so I know the code is right.

While the clients are booting as they should via RDesktop, the screen blanks after ~5min, causing the RDP session to lock, only allowing the logged on MS user to get back in. This causes HUGE problems since all the workstations are accessible by all employees.

I am sure this not a Server 08 issue as I have checked and rechecked the applicable GPOs and registry items.

I have checked lts.conf and X_BLANKING=0

Any help on this would be greatly appreciated as I fly out tonight.

Thanks!!!

---

### Post by deadflowr on 2014-10-13
Duplicate thread 
see here
[http://ubuntuforums.org/showthread.php?t=2248284](http://ubuntuforums.org/showthread.php?t=2248284)

Thread Closed

---

