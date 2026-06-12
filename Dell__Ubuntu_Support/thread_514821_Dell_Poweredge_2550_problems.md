---
title: "Dell Poweredge 2550 problems"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by braintease on 2007-08-01
I have a 1GB RAM Dual PIII 1 Ghz Dell Poweredge 2550 Server (like [http://developer.skolelinux.no/machines/dell-poweredge-2550-spec.pdf]("http://developer.skolelinux.no/machines/dell-poweredge-2550-spec.pdf")) 
onto which I want to install the server edition of Ubuntu 6.06 LTS.

The system contains a Dell PERC 3 / Di Controller which I disabled to rule it out as
the source of the problems.

I first used the server edition of the installation CD, the installation succeeds,
but when trying to boot into the installation the system shows a Segmentation fault error and hangs.

The installation of the normal version (using the Ubuntu LiveCD) also succeeds and the
system boots successfully. I don't mind the extra packages being installed, but the installed
kernel is the "normal" i386 version, so it has no smp support for the 2 PIII's.


I then performed "apt-get linux-kernel-server kernel" and  "apt-get linux-686-smp".
When trying to boot into one of these versions of the kernel, the system hangs and boot fails.

When I boot into the normal install I get the following when I perform the 'uname -a' command:
Linux myhostname 2.6.15-28-386 #1 PREEMPT Wed Jul 18 22:50:32 UTC 2007 i686 GNU/Linux

The list of images in /boot

initrd.img-2.6.15-23-386
initrd.img-2.6.15-23-686
initrd.img-2.6.15-23-server
initrd.img-2.6.15-28-386
initrd.img-2.6.15-28-686
initrd.img-2.6.15-28-server

None of the *-686 or *-386 versions I tried resolved the problem.
Anyone have an idea on how to resolve this issue?


PS: Other problems I ran into was that memtest86+ gave errors in the last 200Kb of memory before installation, so I had to disable "USB Support" and "BIOS USB Support" in the BIOS to resolve the problem.

---

### Post by braintease on 2007-08-03
I tracked this issue to a software problem.
The Dell diagnostics software only checks 1 of the 2 CPU's, so when I switched the positions of the CPU's the problem with the second CPU was detected by the diagnostics software.

Nice going Dell, a nice waste of my time. 

(PS: I used Version 5061A0, Rev. A5061 of the Dell 32 bit diagnostics,
I hope this has been resolved in the new release).

---

### Post by mhilliard on 2007-09-06
Braintese,

We tried to upgrade another Dell PowerEdge 2650 to Ubuntu latest version and ran into a problem that the Perc 3 Mirrored HD setup wouldn't work.  We could see the drives but not access them.    

Did you have any RAID type drive array when you upgraded your Dell PE 2550?
I'm not real familiar with the Dell diag. program... do you run this from a floppy or another source HD?  Did you use this program to disable the Dell Perc 3 Disk controller?

Sorry for the newby questions, we just need to get this old equipment running with Ubuntu as soon as possible.  Any HW config tips you can share would be GREATLY appreciated!!

Mark H.
MPls, MN, USA

when you disabled the

---

### Post by braintease on 2007-09-07
In our case we could also see the RAID array in the installation program, but whenever we tried to partition the drive, the screen flickered and then returned to the main partitioning page.

I turned off the RAID controller in the BIOS:
SCSI Enabled, instead of RAID Enabled. This turns off the PERC3 RAID Controller.

However this didn't solve our partitioning problem. (Maybe for you it will). We had to remove one of the CPU's (which seemed to be defective (see previous posts)) after that the install went through fine.

To download the diagnostics utility:
Dell 32-Bit diagnostics: [http://support.dell.com](http://support.dell.com)
Drivers and Downloads --> Product --> Servers, Storage and Networking --> PowerEdge Server --> 2550

Under Diagnostics you will find an option Dell - Diagnostics Utility
32 Bit Diagnostics.
Download the EI5061A0.ZIP (iso image) and burn it to a CD.
You can then startup from the CD and run the diagnostics.

---

### Post by davit on 2007-10-12
I have the same dell 2550 specification but Ubuntu Server install CD fails at 18% package loading.

I tried various ISO image burns and speeds but with the same result. I have validated the live- CD install integrity on other PCs and the CD is OK but not on the Dell 2550.  

Last install attempt fails at 18% loading Libcb-udeb packages. fed up with burning new ones so it must be the Dell 2550 issue. 

braintease , Let us know what you did to get past my issue?

---

### Post by braintease on 2007-10-13
I did not encounter that problem, so I don't know how to resolve.
See my earlier post for downloading the diagnostics software from the Dell website. It could be a hardware issue.

PS: I disabled the Perc RAID Controller in the BIOS, I only use SCSI mode - so I don't know if that can be the cause of your problems.

The errors you get regarding the mainboard issues within the diagnostics software can probably be ignored safely.
CPU problems however _are_ serious. When the first run of the test goes correctly, run it once more after switching the CPU's. I encountered a problem that the diagnostics software only checks the CPU in socket 1. 

If you don't encounter any problems I would try running a newer version of Ubuntu or another Linux distro to see if that works correctly.

---

### Post by racermd on 2007-11-09
> **davit said:**
> I have the same dell 2550 specification but Ubuntu Server install CD fails at 18% package loading.

I tried various ISO image burns and speeds but with the same result. I have validated the live- CD install integrity on other PCs and the CD is OK but not on the Dell 2550.  

Last install attempt fails at 18% loading Libcb-udeb packages. fed up with burning new ones so it must be the Dell 2550 issue. 

braintease , Let us know what you did to get past my issue?

I'm currently trying to get Gutsy desktop and server to install.  Both have the same issue where it fails part-way through either loading or installing (depending on which disk I'm using).  Again, the CDs I'm using check out fine on all my other hardware.

I don't have any specifics about what might be wrong, but it appears to be a problem with the slim CD-ROM drive in the 2550.  I've got two units that fail to read the Ubuntu CDs and all other CDs work fine.

Luckily, I have a full-size SCSI CD-ROM drive that I was able to connect while the top of the chassis is open.  It's only a 20x read so it's kinda slow and getting the config correct is a little tricky, but it gets the job done.

---

