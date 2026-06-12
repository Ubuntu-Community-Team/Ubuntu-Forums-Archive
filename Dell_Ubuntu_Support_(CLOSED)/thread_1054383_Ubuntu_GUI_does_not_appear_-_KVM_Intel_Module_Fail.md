---
title: "Ubuntu GUI does not appear - KVM_Intel Module Failure"
date: 2009-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hawaiihaole on 2009-01-29
Hi,

I'm a Linux noob, with Ubuntu in particular and forgive me if this is a no brainer for you all.  Having a Ubuntu GUI problem.

I installed Ubuntu 8.10 kernel 2.6.27-7-server without any issue and when I'm first booting up everything starts fine with the exception of a failed kvm_intel module and there is no Ubuntu GUI. After reading several posts here it's fairly obvious that the two issue are linked, maybe related to my video card, not sure.  So I typed: 

sudo lsmod | grep kvm 

It does list the kvn module as: 142784 0, so i know Ubuntu sees it.  I tried to start it:

sudo invoke-rc.d kvm start 

But i get this response:
kvm: disabled by bios
FATAL: Error inserting kvm_intel (/lib/modules/2/6/27-7-server/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported
*Module kvm_intel failed to load
invoke-rc.d: initscript kvm, action "start" failed

So it looks like something related to vm is turned off in the BIOS. Dug through that and thought it might have to do with enabling Virtualization (previous sugg threads)
1. I enabled Virtual Machine Monitor so it can utilize the add'l hw capabilities provided by Intel Virtualization Tech.
2. Enabled VT for Direct I/O - VMM can utilize the add'l hw capabilities provided by Intel Virtualization Tech for Direct I/O/
3. Enabled Trusted Execution - Measured VMM can utilize the add'l hw capabilities provided by Intel Trusted Execution Tech.  The TPM, Virtualization Tech, and Virtualization Tech for Direct I/O must be enabled to use this featured.
4. Enabled TPM as instructed below.

No affect.

Did a BIOS upgrade to A12

Same thing...:(

Anyone have any suggestions for me?  I feel like i'm close...

---

### Post by linabo on 2009-04-04
Hi,

I had the exact same message on a Dell Poweredge T100, Quad Core Intel® Xeon® X3360.

I enabled VT in the BIOS:
1 Press <F2> in the POST screen to go to the BIOS setup.
2 Navigate to the CPU Information section.
3 Press <Enter> and navigate to Virtualization Technology.
4 Select Enabled by toggling the left and right arrow keys.
5 Save the selection and exit the BIOS setup.

This worked for me after a reboot.
I use 'Ubuntu Server 8.10 amd64' and chose Install option 'install minimal virtual server'. I installed server packages OpenSSH and Virtual Machine Host.

---

### Post by raghaven.kumar on 2009-04-30
> **linabo said:**
> Hi,

I had the exact same message on a Dell Poweredge T100, Quad Core Intel® Xeon® X3360.

I enabled VT in the BIOS:
1 Press <F2> in the POST screen to go to the BIOS setup.
2 Navigate to the CPU Information section.
3 Press <Enter> and navigate to Virtualization Technology.
4 Select Enabled by toggling the left and right arrow keys.
5 Save the selection and exit the BIOS setup.

This worked for me after a reboot.
I use 'Ubuntu Server 8.10 amd64' and chose Install option 'install minimal virtual server'. I installed server packages OpenSSH and Virtual Machine Host.

Thanks man, that worked for me too
=D>
I am having the same ubuntu server 8.10 amd64.

PS: btw, i have my server on a raid 5, have to give dmraid -ay to get the partitions detected on every boot.
You facing any similar issues?

---

### Post by unlotto on 2009-08-16
The virtualization switch is under POST BEHAVIOR in m1330 bios A12. Great Place for it, huh?

[http://techiscool.com/flash/M1330bios.swf](http://techiscool.com/flash/M1330bios.swf)

---

### Post by abinadi on 2009-09-13
I have the same problem on my Dell PowerEdge SC1425 with Jaunty but find no reference to Virtualization Technology in the Bios and am now at a loss :(

---

