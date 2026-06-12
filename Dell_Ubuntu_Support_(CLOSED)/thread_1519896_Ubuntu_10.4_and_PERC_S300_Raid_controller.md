---
title: "Ubuntu 10.4 and PERC S300 Raid controller"
date: 2010-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jtuckerxo on 2010-06-28
Hi all,

I have a Dell PowerEdge R410 server that uses the integrated PERC S300 raid controller.  I only have 2 disk drives that were initially setup for raid1 mirroring.  When trying to install Ubuntu 10.4 x64 the setup program cannot find any disk drives.  I have tried using both the megaraid_sas, and mpt2sas drivers that come packaged with Ubuntu.  Just for kicks I tried to use some Dell megaraid_sas drivers that were compiled for Red Hat and SUSE linux distros, but those failed as expected.

I have changed almost every configuration option I can:
- Disabled Integrated SAS controller
- Setup drives for NON-Raid.
- Enabled ATA with and without the SAS controller enabled.
- Tried all the megaraid drivers that come with Ubuntu.

I am running out of options for Ubuntu 10.4 x64.  I am now going to try and install 32-bit version, and Ubuntu 9.10 to see if that makes a difference although I really would like version 10.4 and its necessary for the OS to be 64-bit due to the processing work I will be using this machine for.

If anyone has gotten Ubuntu 10.4 to work with the PERC S300 controller I would love some advice to get mine going, otherwise I think I'm going to have to go back to the colo and bypass the controller all together and just use SATA.

Thanks in advance!
J

---

### Post by jtuckerxo on 2010-06-28
Sorry, forgot to add that I am using the SERVER version of Ubuntu in all cases.

J

---

### Post by jtuckerxo on 2010-06-29
Update:  Tried using Ubuntu 9.10 but that didn't work.  It doesn't have the mpt2sas driver either.  Still looking for help here.

Note:  This thread will also serve to document my attempts to get this running.  Hopefully this information will help someone, or if I finally get it working I will post some instructions on how I did it.

-J

---

### Post by donut87 on 2010-08-09
You may want to read [this]("http://blog.bashton.com/2010/using-a-dell-s300-raid-card-under-linux/")...


Ciao

Donut

---

### Post by jtuckerxo on 2010-08-09
> **donut87 said:**
> You may want to read [this]("http://blog.bashton.com/2010/using-a-dell-s300-raid-card-under-linux/")...


Ciao

Donut

Good article.  Actually this sums up my findings.  I forgot to post my solution so here it is:

PERC S300 does NOT work with linux, its a windows only fake raid controller.  When I called dell support they recommended we buy the SAS6/iR which did not work either.  It seemed like basically the same exact card.  

If you want to use linux on a dell poweredge you should get another raid controller.  We ended up going to FRY's and buying a raid controller (Sorry don't have the model).  I'm sure you could alternatively bypass the raid controller all together if you can get cables that work because the one's dell provides are proprietary I believe.

---

### Post by jtuckerxo on 2010-08-09
Trying to mark this thread solved but I can't seem to find an option anywhere for that...

---

