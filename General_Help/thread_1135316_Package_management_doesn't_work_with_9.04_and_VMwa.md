---
title: "Package management doesn't work with 9.04 and VMware Workstation"
date: 2009-04-24
forum: General Help
---

### Post by kaimi&#326;iece on 2009-04-24
I decided to test Jaunty Jackalope on VMware Workstation 6.5, and I've since found out that I can't use package management there. This is the error I get on Ubuntu 9.04 x86:
[INDENT]This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudu apt-get install -f'.[/INDENT]
Running the commands gives me different errors and doesn't fix the problem. I've deleted that installation so I can't post them at this time. I also installed Kubuntu 9.04 x64, and this is the error message KPackageKit shows when I try searching the packages:
[INDENT]Message did not receive a reply (timeout by message bus)[/INDENT]
When I try to update, I get this:
[INDENT]Package cache could not be opened[/INDENT]
Could it be that VMware is somehow actively screwing with the installation? Any hints would be appreciated.

---

### Post by PA_Dummy on 2009-04-24
I had a problem in that sudo would not work.

From a collection of other posts I did the following.

Boot in safe mode.

Open the terminal window.

Change the first line of the /etc/group file.  Change the 1006 to 0 (zero).  Use V1 or other non GUI editor.

chgrp root /etc/sudoers

chown root:root /etc/sudoers

reboot

test if apt-get works

Perhaps others can expand on the "guts" of the problem

_

---

### Post by kaimi&#326;iece on 2009-04-24
The UID of root is already 0.

---

### Post by kaimi&#326;iece on 2009-04-24
The problem is solved. I deleted some aptitude related files and ran 'apt-get update', and everything is working now. I think the problem was caused by my ISP messing with HTTP connection content during the installation. They were replacing every document with a message reminding me I'm late on my bill. It's also a failure on Ubuntu's part, because such things should be verified before accepting.

---

