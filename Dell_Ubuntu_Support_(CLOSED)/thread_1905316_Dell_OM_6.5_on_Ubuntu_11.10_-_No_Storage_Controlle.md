---
title: "Dell OM 6.5 on Ubuntu 11.10 - No Storage Controllers Detected"
date: 2012-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jladew@calmetrics.com on 2012-01-06
Hello,
I have an R610 using PERC 6/i and it is RAID 10. Ubuntu Server 11.10 is installed and I have installed OM 6.5 based on the following link: [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest).
Everything appears to have installed properly. I install the srvadmin-all option. I start the web server and go in. Under the "Storage" section, I get the "No storage controllers detected". I also run *omreport storageservices* and I get the same message.

Any clues here? Is the package missing a dependency I need to get loaded?

For me the main reason for installing Open Manage is not only to monitor he server but to manage the RAID and its disk space. 

Another question regarding the OM 6.5. If I put 2 more disks in the R610, will I be able to add the disks to the current RAID set/virtual disk or create a new virtual disk via OM6.5 or will I need to boot into the RAID controller BIOS and do it there. I would like to do it where there is no down time to the server. 

Thanks!

Jason

---

### Post by elvar on 2012-02-24
> **jladew@calmetrics.com said:**
> Hello,
I have an R610 using PERC 6/i and it is RAID 10. Ubuntu Server 11.10 is installed and I have installed OM 6.5 based on the following link: [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest).
Everything appears to have installed properly. I install the srvadmin-all option. I start the web server and go in. Under the "Storage" section, I get the "No storage controllers detected". I also run *omreport storageservices* and I get the same message.

Any clues here? Is the package missing a dependency I need to get loaded?

For me the main reason for installing Open Manage is not only to monitor he server but to manage the RAID and its disk space. 

Another question regarding the OM 6.5. If I put 2 more disks in the R610, will I be able to add the disks to the current RAID set/virtual disk or create a new virtual disk via OM6.5 or will I need to boot into the RAID controller BIOS and do it there. I would like to do it where there is no down time to the server. 

Thanks!

Jason

Did you find a solution to this? I am having the same problem.


Regards,

---

### Post by Volans on 2012-03-08
Same problem here, but I have noticed that depends on the kernel that I choose on boot:

 - with a 2.6.32-5 the storage section reports all the informations (enclosures, physical disks, virtual disks, battery, firmware, etc)
 - with a 3.2.0-0 the storage section says "No storage controllers detected."

Maybe some srvadmin-all dependencies does not work well with Kernel 3.x?

---

### Post by Volans on 2012-03-27
I have found that the OMSA Linux packages does not handle correctly the 3.x Kernels.

A workaround was posted here:
[http://lists.us.dell.com/pipermail/linux-poweredge/2011-November/045543.html](http://lists.us.dell.com/pipermail/linux-poweredge/2011-November/045543.html)

I have tried the workaround and it works!
Hoping that the DELL team will soon release a new version of the Linux packages that fixes the problem.

---

### Post by elvar on 2012-03-28
> **Volans said:**
> I have found that the OMSA Linux packages does not handle correctly the 3.x Kernels.

A workaround was posted here:
[http://lists.us.dell.com/pipermail/linux-poweredge/2011-November/045543.html](http://lists.us.dell.com/pipermail/linux-poweredge/2011-November/045543.html)

I have tried the workaround and it works!
Hoping that the DELL team will soon release a new version of the Linux packages that fixes the problem.


Nice! Thank you for sharing this information as this fixed my problem as well.

Kind regards,

---

### Post by ewills on 2012-05-11
Legend. Created an account to say thanks for the reply!

Confirmed working on Ubuntu 12.04 LTS

---

### Post by SleepIT on 2012-08-28
> **Volans said:**
> I have found that the OMSA Linux packages does not handle correctly the 3.x Kernels.
 
A workaround was posted here:
[http://lists.us.dell.com/pipermail/linux-poweredge/2011-November/045543.html](http://lists.us.dell.com/pipermail/linux-poweredge/2011-November/045543.html)
 
I have tried the workaround and it works!
Hoping that the DELL team will soon release a new version of the Linux packages that fixes the problem.
 
Thank you very much for this link.  It saved my day!!!

---

