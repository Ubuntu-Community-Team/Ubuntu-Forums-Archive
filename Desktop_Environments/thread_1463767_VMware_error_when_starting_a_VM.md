---
title: "VMware error when starting a VM"
date: 2010-04-27
forum: Desktop Environments
---

### Post by trubendall on 2010-04-27
I installed VMware Workstation 7.0.1 build 227600 on my Ubuntu 10.04 x64 (Release Candidate) workstation and everything worked great.  I installed my OS (Windows XP Pro) and apps and everything worked.  Now, I restarted my computer and cannot launch the XP Workstation.  VMware Workstation launches, but once I try and launch my VM I get the following errors.

 

"Could not open /dev/vmmon: No such file or directory.  Please make sure that the kernel module 'vmmon' is loaded."

 And after hitting OK I get

"Failed to initialize monitor device."

Then after hitting OK again I get

"Unable to change virtual machine power state: Cannot find a valid peer process to connect to"

 

Any help would be great.

 

Thanks,

---

### Post by vmpho on 2010-05-01
It looks like VMWare did not start automatically after system reboot.

I found the following command from a forum and it works but  I need  to re-run every time system reboot.

sudo service vmware start

Still investigate how to fix it. I run Ubuntu 10.04 32-bit production version with fresh install.

:confused::confused::confused::confused::confused:

---

### Post by jtliii on 2010-05-24
Thanks. That is a useable workaround for now. I hope it gets fixed soon. Mine has been somewhat random. Sometimes the service starts on its own other times it doesn't.

---

