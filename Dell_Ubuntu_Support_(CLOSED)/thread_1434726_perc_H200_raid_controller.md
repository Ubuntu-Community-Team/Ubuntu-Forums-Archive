---
title: "perc H200 raid controller"
date: 2010-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tomcarly on 2010-03-20
Hi,

i have a poweredge R610 with a perc H200 integrated raid controller for my hard disks. During the installation of Ubuntu 9.10 or 8.04, the hard disks are not recognized. I assume this is because the raid controller is not supported. RedHat supports this raid controller, but i haven't been able to compile this driver for Ubuntu. Does someone maybe have an idea how to solve this?

Thanks,

Tom

---

### Post by jrssystemsnet on 2010-03-20
> **tomcarly said:**
> Hi,

i have a poweredge R610 with a perc H200 integrated raid controller for my hard disks. During the installation of Ubuntu 9.10 or 8.04, the hard disks are not recognized. I assume this is because the raid controller is not supported. RedHat supports this raid controller, but i haven't been able to compile this driver for Ubuntu. Does someone maybe have an idea how to solve this?

Thanks,

TomHave you configured the disks in a RAID array already via the controller's BIOS?  Because I recently converted an existing PowerEdge server with the same controller and an existing RAID1 mirror from Windows Server 2003 to Ubuntu 9.10 server, and the installer picked up the array with no problems.

---

### Post by tomcarly on 2010-03-20
It's a brand new machine without OS on it, and i didn't do anything in the BIOS yet. Thanks for the suggestion, i'll give it a try. Is it straight forward to do this? (i've never had to do it)

---

### Post by tomcarly on 2010-03-22
Hi,

still no luck. I have been able to install CentOS on it, so i really think it is a driver problem. Does someone maybe have an idea how to get this driver for ubuntu?

---

### Post by jfabrizio on 2010-03-26
I have tried to install ubuntu on my new server (see this [thread]("http://ubuntuforums.org/showthread.php?p=9029610#post9029610")).
I have having your same problems because the installation was stopped on the "Detect disks".

The message error is this: 
```
"No disk drive was detected. If you know the name of the driver  needed  by your drive, you can select it from the list" 
```

But, I tried to run ubuntu-desktop from cd. Ubuntu started correctly, therefore I   launched GPARTED and I saw these partitions:

- sda1 (fat32): 73MB
- sda2 (lvm2): 8 GB --> Inf: Logical volume Management is not  yet   supported
- sda3 (ext3):  213 MB
- sda4 (extended): 496 GB
    - sda5 (swap): 2 GB
    - sda6 (lvm2): 454 GB -->Inf: Logical volume Management is not    yet supported

So, I don't understand if the ubuntu-desktop, unlike ubuntu-server, detects correctly the raid controller and the raid disk. Is it possible?

Thanks.

---

### Post by jfabrizio on 2010-03-26
Note: The server works correctly with Suse Linux Enterprise Server, but I'm going to install ubuntu because this environment is more familiar than Suse (apt vs yast, the location of main files, the community :) )

Can anyone help me?

Thank

---

### Post by jrssystemsnet on 2010-03-26
What are the versions of Ubuntu you've tried?

For reference, the Dell server with PERC controller I successfully installed on without any problems is running Karmic - I have another server at the same client which required Karmic to support the SATA controller on the motherboard, so I went ahead and used Karmic on everything there.

It's entirely possible that the drivers for the PERC were not present in Hardy.

---

### Post by jfabrizio on 2010-03-26
I tried ubuntu-server 9.10 a 64 bit (the installation was stopped on disk detection) and ubuntu-desktop 9.10 a 64 bit. Both versions was downloaded few day ago from official ubuntu web site.

I'm seeing on ubuntu web site that there are two server version: Ubuntu 9.10 Server (maintained until 2011) and Ubuntu 8.04 LTS Server (maintained until 2013). Are there critical differences between the two version? ..in direction of raid controller?

Thank.

---

### Post by jrssystemsnet on 2010-03-26
> **jfabrizio said:**
> I'm seeing on ubuntu web site that there are two server version: Ubuntu 9.10 Server (maintained until 2011) and Ubuntu 8.04 LTS Server (maintained until 2013). Are there critical differences between the two version? ..in direction of raid controller?Normally, one should use the LTS version for production server installs.  It is possible that the newer version (in this case, 9.10) may have hardware drivers available that the LTS version did not.  In my case, a completely separate server required a SATA driver in 9.10, so I did 9.10 installs to both that server and the one with the PERC controller.

Now that I look at it, we have different *models* of PERC; I'm sorry for the confusion:

> /var/log/kern.log.0:Mar  8 14:23:51 mxbackup kernel: [   84.919184] scsi 0:2:0:0: Direct-Access     DELL     PERC 5/i         1.03 PQ: 0 ANSI: 5
/var/log/udev:ID_MODEL=PERC_5i

Mine has a PERC 5i controller, not a PERC 200.  Sorry for the mixup. :(

---

### Post by reiki on 2010-03-26
The H200 is a newer controller compared to the PERC line. The H200 and H700 are basically "poor man's raid" as they don't have all the guts of the PERC controllers. That's probably why the PERC controllers are found, but the H-series controllers aren't. 

Therre's a bug on this. This is what I found in it...
```


Having the same problem with debian, it might not be ubuntu related. I have checked all the scsi*.udev packages and so far failed to find the mpt2sas.
Solution I used was to extract the /lib/modules/<kernelversion>/kernel/drivers/scsi/mpt2sas/* and place them in the initrd.gz file.

Note: I use PXE booting so changing the initrd file was relatively quick.
Note: last installer checked used kernel 2.6.30

```

---

