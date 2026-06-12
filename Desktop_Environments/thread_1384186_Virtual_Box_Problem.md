---
title: "Virtual Box Problem"
date: 2010-01-18
forum: Desktop Environments
---

### Post by Ceiber Boy on 2010-01-18
Hi

I'm running Ubuntu 9.10 - the Karmic Koala (64-bit)- released in October 2009. in every way it works perfectly, from the repository using the synaptic package manager i installed virtual box (VB) to run windows XP (32-bit). 

when i installed everything went well and i was able to install and run without problem XP in VB, however upon rebooting the computer i opened VB and then tried to start XP, then i was confronted with the following Error messages:

  p, li { white-space: pre-wrap; }  *Failed to open a session for the virtual machine WinXP.*
 *Virtual machine 'WinXP' has terminated unexpectedly during startup.*
 

  p, li { white-space: pre-wrap; }  [I]Kernel driver not installed rc = -1908

Please install the virtualbox-ose-source package[/I]
 i followed the instructions and reinstalled 'virtualbox-ose-source package' again using the synaptic package manager. again it worked immediately but upon rebooting my machine it constantly returns to the same problem. I have also tried downloading VB direct from sunmicro systems but still have the same problem.


[U]Questions
[/U]How do i fix this problem?
Is VB from the repositories 64-bit?

Any help would be greatly appreciated as i am a Linux convert and now loath using windows but an forced to due to software used by my employer that will not run on wine!

Regards

---

### Post by Lars Noodén on 2010-01-18
> **Ceiber Boy said:**
> ...due to software used by my employer ...

Which software and for what task?

---

### Post by Mia1990 on 2010-01-19
I have tried running virtual box not the ose but the one downloaded from sun as virtualbox OSE does not have usb support that being said you may have to add it to your user settings systems>administrations>users and groups.Click your user name amd go down to click to make changes enter your password and see if virtual box is in there if not add it and see if that helps any.

---

### Post by Kendall_Tristan on 2010-01-19
I had similar issues from the VirtualBox in the repository.  I had to reload the kernel driver every time I wanted to run it.  The solution for me was to purge VirtualBox and get a newer version from Sun's website.

---

