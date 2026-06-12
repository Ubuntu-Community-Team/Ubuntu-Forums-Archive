---
title: "Ubuntu for dell dimension 9200"
date: 2007-08-15
forum: Dell  Ubuntu Support
---

### Post by mwang_2008 on 2007-08-15
I just bought Dell Dimension 9200 with Window Vista installed.  I want to install Ubuntu to make it dual boot. 

I download the Ubuntu and following below url to create Ubuntu CD
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I Partitions resizing my hard drive and following url to instll 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

The problem:
Once trying to boot from Ubuntu CD, it displays "No boot device available" 

Can anyone tell me how to correct it. 

Thanks.

--Michael

Here is the system config:
 Dim 9200, Intel Core 2 Quad Core Processor Q6600 (2.4GHz,1066FSB) with 8MB cache  
 2GB DDR2 SDRAM at 667MHz  
160GB SATA II Hard Drive (7200RPM)

---

### Post by ridgeland on 2007-08-16
Did you check that the BIOS is set to allow boot from CDs?

That is an awesome PC.

Have you ever booted from the CD drive?  

There are other distros you could download and burn to CD that do not load to the hard-drive, just run from the CD.  You could try to download, burn and boot one of those.
For suggestions:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
This is a System Rescue CD that I use in addition to Ubuntu, I've find it useful.  See if you can get it to boot (small download about 200MB maybe).  It boots to text not fancy graphics but you can see if it works.

---

### Post by gonesolo on 2007-12-12
Have a Dell 9200 myself and am just downloading the "alternative" cd because the live CD does not work with my 8800GTX.

However do you have RAID enabled in the bios? If the SATA controller is in RAID mode then Ubuntu may not recognise it. I had this problem in the past with 7.04 on a different machine, Ubuntu would recognise the drives fine in normal but once I enabled RAID it could not find the controller.

Maybe drivers have been updated but it might be worth a try 


(be carefull though if you disable RAID and you have arrays setup you may loose your Windows OS and files so make sure you have a backup first)

---

