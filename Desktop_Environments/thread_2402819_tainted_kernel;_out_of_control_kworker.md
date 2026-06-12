---
title: "tainted kernel; out of control kworker"
date: 2018-10-04
forum: Desktop Environments
---

### Post by Peter_Brandon on 2018-10-04
I'm running Ubuntu w/ a KDE desktop.

dmesg, right after I start up gives me these errors:

PKCS#7 signature not signed with a trusted key
vboxdrv: loading out-of-tree module taints kernel.
vboxdrv: module verification failed: signature and/or required key missing - tainting kernel

I also have a kworker process that runs at 85%+ continuously.  Doing a backtrace w/  echo l > /proc/sysrq-trigger (after a echo 1 > /proc/sysrq-trigger), I get a backtrace in dmesg, with for example:
CPU: 0 PID: 9603 Comm: kworker/0:2 Tainted: G           OE    4.15.0-36-generic #39-Ubuntu
CPU: 6 PID: 0 Comm: swapper/6 Tainted: G           OE    4.15.0-36-generic #39-Ubuntu



From [https://www.suse.com/support/kb/doc/?id=3582750](https://www.suse.com/support/kb/doc/?id=3582750), I learned that G OE indicates a tainted fully-GNU kernel that is out of tree (meaning?) and has a missing or bad signature.   So, my guess here is that vboxdrv isn't properly signed and that this taints the kernel and somehow gets the kworker process (0:2 that time) to run continuously.

So, what to do?  I figured if I created and applied my own signature to the kernel module, that would do the trick.  I followed the prescription in the first answer here: [https://askubuntu.com/questions/760671](https://askubuntu.com/questions/760671) .  This walks me through creating signing keys, signing the module, confirming the module is signed w/ the key (it was and still is), and registering the key w/ Secure Boot.  It then says I should reboot and sends me to a page that explains how to enroll MOK.  

I didn't do this enroll MOK part because a) I have Secure Boot off in the BIOS, b) when I try to turn on Secure Boot in the BIOS it informs me that there is no trusted key (or something like that) and won't let me turn it on, and c) none of my other kernel modules are complaining about being tainted.  I figured I just needed to sign vboxdrv with something.  

Well, it didn't work.  I get the same dmesg errors at startup as before and my kworker process (today 0:0) is working away.  Would probably help to know that I'm running an all new Dell.  Anyone have any suggestions?

---

