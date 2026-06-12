---
title: "SAM 2003 on Ubuntu"
date: 2007-10-05
forum: Education &amp; Science
---

### Post by Barbank on 2007-10-05
Hello, i'm fairly new to this awesome community. I just installed Ubuntu 7.04 the other day and  was wondering if I could run SAM 2003 on here.

What is SAM 2003?
I'm taking a Intro to Computer Information System course. The course was originally set up for SAM 2007 but the company said the software was not available for this semester. So we downgraded to SAM 2003.

The software is an emulation software. It trains us on how to us MS Office. NO instances of office are required to run it. The box just says either Windows XP or Windows 2000 must be installed.

I installed the latest version of Wine and it's not listed as a program available in there. I did get into the IRC chat for Wine, but they couldn't help me. 

I just would like to know my options here. I DO have a Windows 2000 computer, but it's my mom's and I wouldn't be able to train when I want to. I'd prefer it if I could run the CD on Ubuntu. I do not have a version of Windows because upon installing Ubuntu, I did not think to dual-partition anything and you can guess what happened.

My other option is to have Windows reinstalled by CD which will cost me $75 (best offer I've gotten that's willing to acknowledge Linux)

Then of course there's getting a recovery CD from the manufacturer which is around $25 then get the drive dual-partitioned, etc.

I hear dual-partitioning causes stuff to be slow.

My goal is NOT to pay, but if I have to pay to get it running, i supposed that will suffice depending on the price.

I would appreciate any help on this.
Thanks.

---

### Post by PilotJLR on 2007-10-05
If this apps doesn't work with wine, then you can choose to either dual-boot Windows and Ubuntu, or use VMware Server or VirtualBox (both free) to run a virtual instance of Windows.

Note that doing the latter requires a copy of XP that is NOT a manufacturer recovery CD (since those 90% of the time will not work on virtual hardware). If you are a college student, your college bookstore likely sells cheap XP acad licenses.

For dual booting, nothing is slowed down. Except for the downtime as you reboot...

---

### Post by b15h0p7 on 2007-10-05
> **Barbank said:**
> I hear dual-partitioning causes stuff to be slow.
That is one of the most incorrect things I heard in my life.  Dual-Booting/Dual Partitioning does nothing of the sort, but gives you the best of both worlds as some people say =)

---

### Post by Adam_GUI on 2007-10-05
I'm using SAM software myself.  "Networking Academy" for a course this quarter.

Unfortunately, it's integrated with Internet Explorer.
It doesn't play nice with firefox.

You can try running the program through crossover office + explorer 6.
I've got explorer running in BSD, but all the active X is disabled....so for me, Windows is the best option to run the software.

BTW, in your copy, are the *.swf view files not loading?
It's a problem we're having with the software.

---

### Post by Barbank on 2007-10-06
Ok, I tried to install Virtualbox and it was doing something but whatever it was doing it was stuck on the screen forever. I tried to close it but nothing happened. I couldn't figure out the equivelant of Ctrl+ALT+DEL so I restarted. Now when I try to install anything, especially even open the package manager, it gives me:

E: Dynamic MMap ran out of room
E: Error occured while processing itcl3.1 (NewFileDesc2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

OR it says Virtualbox needs to be reinstalled but no archive can be found. I tried installing other software (from kde-apps.org) and this is a hurdle in the way.

I'm also trying to install Hava to run the new app from kde-apps but this is blocking it as well.

---

