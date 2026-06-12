---
title: "check for running process and warn about running process on shutdown/reboot"
date: 2011-05-16
forum: Desktop Environments
---

### Post by crypticlabs on 2011-05-16
Hello,

After booting/rebooting Ubuntu, I manually run an alias that starts a VirtualBox Windows virtual machine in headless mode. I then interact with this VM using RDP.

Often, I will poweroff or reboot Ubuntu and forget to properly shutdown the VM. I'm looking for a way to either:

a) hold of or prevent a shutdown/reboot and warn me that the VM is still running (perhaps by checking the process list for a pattern that matches this VM) so that I can properly shutdown the VM. I believe this occurs if there is an unsaved document of 'gedit' open.

b) run a shutdown script that will properly shutdown or pause the running VM.

I should be able to script both examples but I'm not sure where/when to place/run the scripts.

Thanks!

---

### Post by crypticlabs on 2011-05-16
One more thing - I'm mainly interested in option "a". I know there are plenty of "how tos" on running shutdown scripts. I would prefer to get a warning and halt the initial shutdown/reboot so that I can manually shutdown the VM myself.

---

### Post by dwitkin on 2011-08-02
I don't have an answer, but I second the question!  This happens to me all the time, where I forget to shutdown a virtual machine.  A way to generate a warning or to suspend the VM would be great.

---

