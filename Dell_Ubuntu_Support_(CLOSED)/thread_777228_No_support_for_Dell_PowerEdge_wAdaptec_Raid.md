---
title: "No support for Dell PowerEdge w/Adaptec Raid?"
date: 2008-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbeiter on 2008-05-01
I have tried loading 7.04 and just tried to load 8.04 and I am seeing the same problems. The installation goes fine, partitioning, formatting, and package selection goes fine. When it is time to reboot, I get the following errors upon boot:

aacraid: Host adapter reset request. SCSI hang ?

I see this is a common problem searching the web with "Ubuntu aacraid: Host" with no resolutions to be found.

Is there no fix for this? You simply can not change your Dell PowerEdge servers into opportunities to show the power of Ubuntu in the corporate datacenter?

There are a LOT of PowerEdge systems moving into retirement out there that could be put to excellent use. Sadly, a missed opportunity for Ubuntu to move beyond the desktop.

If there are any work-arounds or different ways to set up the disks in the raid controller, please let me know. I would rather use Ubuntu but will move on to Fedora if it isn't up to the job.

---

### Post by aidave on 2008-05-01
You can try Debian, if you still want apt.

I have Ubuntu running on a PowerEdge but no problems with RAID (Im not sure if its the same setup as yours though).  I did have major trouble trying to get the Ubuntu's GRUB installer to work.

CentOS is a rock solid choice for PowerEdge as well.

---

### Post by barichardson5727 on 2008-05-02
Which PowerEdge server is this? You stated that you tried 7.10 and 8.04, but what version desktop/server/alternate? 

I can only assume that since you are stating that your server has an adaptec controller that it is something like a PE2650 with a PERC3/di raid controller. If there is no way to get the server to operate on ubuntu in raid mode you can always go to the server bios and switch to scsi mode and use mdadm for a software raid. Actually, a software raid will outperform a perc controller anyway. It will just require more work if a disk needs to be rebuilt since you cant just pop a disk into the server and expect it to rebuild automatically.

---

### Post by jbeiter on 2008-05-02
Yes, it is a PERC3. Someone mentioned there may be a flash upgrade that might support linux that we are going to try. If that doesn't work, I'm going to try your suggestion and switch to scsi mode.

Thanks!

---

### Post by Kolipoki on 2008-05-19
Hi all,

Voilá!

I was able to fix this problem just today May/22/08, by updating the firmware of the Adaptec raid controller PERC3/Di (Although I also upgraded the BIOS to Revision A21). My system is also a Dell PowerEdge 2650, in Raid 5. 

There's a newer version of the firmware in Dell's site, posted as of Nov/07. File name is BR168380.exe (would put link here to page results, but it's incredibly long). Will need 2 floppies. This file seems to be good for all operating systems (it says so while making the setup disks).

Didn't have to reinitiate setup. Boot came up fine, no hassles.

I agree with the fact that these Poweredge servers should be given a "2nd air". Ubuntu Server Edition should be a good choice for them. At least I'll try and see... 

I hope this info helps...

---

### Post by barichardson5727 on 2008-05-20
Just to add one thing that pertains to Adaptec controllers on Dell servers when applying firmware updates. Following this procedure can make things go smoothly and will make sure that all critical issues are patched on your controller.

When doing firmware updates on an Adaptec controller you need to perform all updates in the order they were released without skipping any revisions between your current version to the latest version. Firmware updates for adaptec controllers do not build upon each other like with most updates, therefore it is important that you don't skip any of the firmware revisions when performing the updates. You do not have to follow this procedure with the LSI controllers, you can just jump to the latest version without any worries.

If you just skip to the latest version you could be very well missing some very important updates that will affect the overall stability and performance of the controller and disk array. 

Its also a good idea to make sure your hard drives are at the latest firmware as well when applying updates. Dell has a bootable cd available that will scan your controller for hard drives that need updates and update everything as needed.

---

### Post by jbeiter on 2008-06-02
It was the PERC firmware. Once we updated the firmware everything was recognized just fine.

Thanks for the help!

---

### Post by xang on 2008-06-09
I just followed this thread and updated my Dell 2650's bios to A21 and the Perc3/QC firmware. Once this was done, Ubuntu Server 8.04 installed like a champ!

---

### Post by lfmiller on 2008-11-16
I can confirm updating the BIOS and the Raid Bios fixed the problem - I am running an older Dell PowerEdge 2400 with PERC 2/SI Was running Ubuntu 6.06 server and decided to upgrade to 8.04 and had the same problem - I updated the BIOS of the machine and fixed no problems now -

---

### Post by lloydrmc on 2008-12-19
On my machine, the 8.04.01 (desktop) wouldn't boot as a live CD, but 6.06.01 (desktop) would.  Upgrading to A21 BIOS did the trick.  I have figured out the disk controller only by inference, because Dell's Model Number and Adaptec's don't even resemble each other.  Haven't applied the controller BIOS update, and I may well leave well enough alone.

---

### Post by samiam24 on 2008-12-25
Any solutions for a Poweredge 2300? I have not tried loading the latest Ubuntu, the last time I did try I would need to disable hardware support for the hard disks.  Is this still the case?

---

### Post by fromans on 2009-01-22
> **samiam24 said:**
> Any solutions for a Poweredge 2300? I have not tried loading the latest Ubuntu, the last time I did try I would need to disable hardware support for the hard disks.  Is this still the case?

Which raid controller does your Poweredge 2300 use? I had the exact same problem as you after installing 8.04 Server LTS on my PowerEdge 2650 with a PERC 3/Di. I was able to solve it by updating the card's firmware as some have already mentioned. Unfortunately, Dell's firmware utility requires booting from a floppy and this is the important part....accessing the Dell Utility partition. **If you don't have the 32MB utility partition Dell puts on their servers, the floppy will just hang at "Loading DRMK version 8.00".** I had to wipe my server, reinstall a Windows OS using the Dell Openmanage disks (making sure to include the Dell Utility Partition option), then flash the card's firmware, and reinstall Ubuntu again. An easy problem to solve, albeit with a stupid methodology required by their update utiltiy floppies. Here's a link to the last PERC 3/Di firmware.

[http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&deviceid=1375&libid=35&releaseid=R168380&vercnt=7&formatcnt=0&SystemID=PWE_FOS_XEO_2650&servicetag=&os=WNET&osl=en&catid=-1&impid=-1](http://support.dell.com/support/downloads/format.aspx?c=us&l=en&s=gen&deviceid=1375&libid=35&releaseid=R168380&vercnt=7&formatcnt=0&SystemID=PWE_FOS_XEO_2650&servicetag=&os=WNET&osl=en&catid=-1&impid=-1)

I hope this helps you!

---

### Post by samiam24 on 2009-01-31
I am using a Dell PERC 2/SC RAID controler.  I cannot recall the version of BIOS I am running but I will check if it is the latest and update the post. 

Here is what I found ont he issue(s)
[http://ubuntuforums.org/showthread.php?t=217667](http://ubuntuforums.org/showthread.php?t=217667)

---

### Post by LinuxUser9 on 2010-04-13
> **xang said:**
> I just followed this thread and updated my Dell 2650's bios to A21 and the Perc3/QC firmware. Once this was done, Ubuntu Server 8.04 installed like a champ!


OK, just one stupid question... how are you using an exe file??? Don't tell me you have to enlist that... that "other beast" just to do it. I'd rather find another distro!

---

### Post by trundlenut on 2010-04-15
I updated the bios on my PE2800 by downloading the update from dell and creating a boot floppy on a windows machine and then boot the server with the floppy in.

Finding a windows machine with a floppy drive was the hard part...

---

