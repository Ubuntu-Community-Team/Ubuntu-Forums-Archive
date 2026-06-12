---
title: "Synaptic error"
date: 2005-11-11
forum: Desktop Environments
---

### Post by installer on 2005-11-11
When I hit the reload button in Synaptic I get the following error any ideas?

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Thanks.

---

### Post by spizkapa on 2005-11-11
It happens some times, don't worry about it. I believe that it's a network problem so that the package you download (packages.gz or some such) isn't the right size and hence fails signature verification.

This shoudln't alarm you because, while it IS possible that another file has the same MD5 sum as the one you're supposed to be getting from Ubuntu, the likelihood of this happening by accident is VERY small, negligible. For this to be a serious issue, it would have to be an external party subverting Ubuntu's repositories and hijacking your traffic. The chances of this are mind bogglingly small.

So, give a while and do another reload, it'll work, assuming that there are no problems on your end and Ubuntu's end of the network.

---

### Post by installer on 2005-11-11
Thanks it was doing it yesterday as well, I'll see if it rights itself. :)

---

### Post by ThirdWorld on 2005-11-11
it happened to me this morning when i was updating Ubuntu.

---

