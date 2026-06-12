---
title: "VMware-workstation-5.0.0-13124 on Breezy"
date: 2005-11-13
forum: Desktop Environments
---

### Post by xbaez on 2005-11-13
Has anybody been able to run this software on Breezy?

I had it working with Hoary, and I was even able to boot my existing WinXP.

Right now I doubt I'll be able to run my existing WinXP (full hard drive support), but if I am able to run it, I can install a WinXP and run it 

When I configure vmware-config.pl, it builds the kernel, it sais is loads perfectly, and when I try to run vmware, it tells me (again) to configure it properly.

Regards

---

### Post by mrshish on 2005-11-13
I had the same problem. The issue is with the kernel, it was compiled with GCC 3.4 instead of 4.0. You either need to update your kernel to 4.0 (what I did) or compile VMware with 3.4.

---

### Post by xbaez on 2005-11-14
ok I'm gonna reboot with the latest kernel 2.6.12, use gcc-3.4 to compile VMware, and see if it works

Thanks for the tip

---

### Post by xbaez on 2005-11-14
I tried compiling VMware-workstation-5.0.0-13124 with GCC
3.3
3.4
4.0
None of them work, vmware-config.pl just doesn't runs, I'll appreciate any ideas since this software is amazing

---

### Post by Hallavej on 2005-11-14
[QUOTE=xbaez]I tried compiling VMware-workstation-5.0.0-13124 with GCC
3.3
3.4
4.0
None of them work, vmware-config.pl just doesn't runs, I'll appreciate any ideas since this software is amazing[/QUOTE]

did you read this one:
[https://wiki.ubuntu.com/InstallingVMWare?action=show&redirect=VmWare+guide%3A+How+to+install+VMware+in+Breezy](https://wiki.ubuntu.com/InstallingVMWare?action=show&redirect=VmWare+guide%3A+How+to+install+VMware+in+Breezy)

"vmware-any-any-update94.tar.gz" worked for me.

---

### Post by suRoot on 2005-11-14
Remove the notconfigured (can't remember the exact name, but something along these lines) file from /etc/vmware.  I had the same problem, and it was just a matter of removing that file after running vmware-config.pl

---

### Post by xbaez on 2005-11-16
I downloaded VMware Beta 5.5, it works good now

however since Hoary 5.04, VMware 5, I haven't been able to boot my already existing WinXP with full hard drive (/dev/hda) support

---

### Post by rkinder on 2005-11-16
[QUOTE=xbaez]I tried compiling VMware-workstation-5.0.0-13124 with GCC
3.3
3.4
4.0
None of them work, vmware-config.pl just doesn't runs, I'll appreciate any ideas since this software is amazing[/QUOTE]

In what way do 'None of them work'? What error messages are you getting? I have successfully installed and run vmware 5 on both 5.04 and 5.10, and managed to run existing (created under 5.04) VMs in 5.10 - not surprising really since they are virtual machines ;)

Please provide more details on errors etc. and I'll see if I can provide some help.

---

