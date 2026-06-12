---
title: "Windows to Ubuntu"
date: 2006-07-21
forum: Desktop Environments
---

### Post by lukeprog on 2006-07-21
First, my abbreviated tale of woe. I ran WinXP and plenty of anti-virus, anti-malware software on my new laptop. Suddenly, I got a virus similar to Sasser that was incurable by any antivirus program. I had to reformat my HD and reinstall and reconfigure everything, which I did, this time with even more anti-malware and all the latest Windows udpates. Less than two weeks later, my computer has another virus, though it won't even be detected by anti-malware scanners or the Task Manager processes list (but everything is suddenly incredibly slow, the internet doesn't work, bootup is 10+ minutes, etc.)

So, screw Windows. I'm moving to Ubuntu. My productivity will decrease for a bit because I'll have to learn new software to do everything, but I can't stand Windows' insecurities any longer.

But I'm wondering: 

1. How do I port all my Thunderbird mail from Windows to Thunderbird on a new Ubuntu install?
2. How can I fix my MBR (in case the virus is there) without a floppy drive (I'm used to doing: DOS boot disk, fdisk /mbr)?
3. What anti-virus, anti-malware should I install for Ubuntu?
4. Is there a decent alternative to Publisher for Linux?
5. Any other recommendations?

Many thanks!

---

### Post by jamesford on 2006-07-21
1: i reckon u can just copy your thunderbird profile folder from xp to linux, might be that u need to reinstall some extensions, not sure (same with firefox)

2: dunno

3: u wont really need any, but there are plenty of threads on this, do a search

4: dunno

5: ubuntuguide.org

---

### Post by aysiu on 2006-07-21
1. Copy C:\Documents and Settings\lukeprog\Application Data\Thunderbird to /home/lukeprog/.mozilla-thunderbird

2. Ubuntu will automatically install its own boot loader to the MBR.

3. None needed.

4. Scribus.

5. Read this: [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) and this [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by lukeprog on 2006-07-22
Thanks, guys.

All of my data is on an external 400GB HD formatted NTFS. Can Ubuntu mount this as anything but read-only? Maybe I'll have to dual-boot Ubuntu and Windows, and only go online with Ubuntu or something.

---

### Post by cptnapalm on 2006-07-22
There is some new thing which I've read about which will (probably) make reading and writing to NTFS relatively unproblematic.

Here is something on migrating your mail from Windows to Linux: [http://gentoo-wiki.com/HOWTO_Transition,_Move,_Migrate,_Switch_Thunderbird_from_Windows_to_Linux_with_Enigmail](http://gentoo-wiki.com/HOWTO_Transition,_Move,_Migrate,_Switch_Thunderbird_from_Windows_to_Linux_with_Enigmail)  It may or may not be helpful to you, but I thought I'd throw it in.

One possibility, if Scribus does not meet your needs, is to try running Publisher under Wine or in a virtual machine, like VMWare.

---

### Post by jimmygoon on 2006-07-22
> **lukeprog said:**
> Thanks, guys.

All of my data is on an external 400GB HD formatted NTFS. **Can Ubuntu mount this as anything but read-only?** Maybe I'll have to dual-boot Ubuntu and Windows, and only go online with Ubuntu or something.

Use at your own risk: [http://digg.com/linux_unix/Instructions_to_install_NTFS-3G_in_Ubuntu_Dapper](http://digg.com/linux_unix/Instructions_to_install_NTFS-3G_in_Ubuntu_Dapper)

---

