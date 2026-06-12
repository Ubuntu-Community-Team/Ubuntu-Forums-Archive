---
title: "Installing 8.04 on a PowerEdge R805 Server"
date: 2009-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Twelveone on 2009-09-25
Hi,

My bosses have just bought a PowerEdge R805 with a single 160GB hard drive and a SAS 6iR Controller.

I have tried installing 32bit Ubuntu 8.04 from the live disk and received the error "HDIO_GET_IDENTITY failed for '/dev/.tmp-8-0"

I then tried the 64bit version of 8.04 and got a Kernel Panic error

Has anyone got any experience of installing Ubuntu on an R805 and can you help me?

I would consider myself more than a novice user but would hesitate to say advanced and have never used a server before.

Cheers

Stewart

---

### Post by kkallsen on 2009-10-02
I have Ubuntu server 9.04 64 bit installed on a Poweredge R805.  The install was iffy, but doable.  My only issues was with the UUID.  My current issue is with slow network cards and ubuntu.

---

### Post by Twelveone on 2009-10-26
Thanks,

After buying a second 160Gb HD and setting up a RAID1 Array I was able to install 9.04 64bit. 

I think there were 2 issues:
 1: 8.04 is not compatible with the R805 server
 2: The Dell utilities will not allow a RAID Array of only one HD and until the Array is set up the installer can't see the HD.

We are still having some issues with speed but that is as much related to our application than anything else.

Stewart

---

