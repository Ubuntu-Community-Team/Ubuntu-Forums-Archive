---
title: "XOrg Freezing My Computer"
date: 2011-01-03
forum: Desktop Environments
---

### Post by ChrisEiffel on 2011-01-03
Hi,

I am running Ubuntu Lucid with Compiz, Cairo Dock, Screenlets, on a Laptop with an i7 Nvidia graphics card.

After I wake my laptop up from a suspend or hibernation I notice that my computer will freeze for several seconds every so many seconds. After looking at the System Monitor I noticed that the application that is stealing all my CPU and causing my computer to freeze is XOrg. 

Here is my xorg information
$X -version
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux Starace 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=3f5b27f9-a191-4b6c-83d8-603b78e36593 ro quiet splash
Build Date: 10 November 2010  11:25:53AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4



I never had this problem before December. I was thinking it may have something to do with ubuntu header 2.6.32 because it was soon after I started having problems.


Does anyone have any theories or ideas as to why XOrg is stealing my CPU?

Chris

---

### Post by zaidaus on 2011-01-04
I'm having similar issues. I don't know why this is happening. It started happening in November for me. I thought my graphics card was broken but now I have no idea what it is. Sometimes it will freeze after I have left the computer idle for a while, and sometimes it will freeze while I'm browsing. It's really starting to frustrate me.

---

### Post by ChrisEiffel on 2011-01-13
The problem *seems* to have fixed itself with the new ubuntu headers. I think they've fixed the issue with the newest update.

---

