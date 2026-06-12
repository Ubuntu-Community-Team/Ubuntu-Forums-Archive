---
title: "heavy IO + firewire traffic locks up system"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Georges on 2006-03-18
Hi

if there is heavy IO going on and I transfer several GB of data to a firewire hardrive, the complete system just locks up. No panic but a complete freeze, including mouse, console switching etc.
I ran a test while switched to the text console. After the crash Alt-SysReq does not respond anymore either. No message on virtual console 1 as well. Even the cursor stops blinking 

So yes, this is a kernel issue. The firewire disk storage driver ist not working correctly!
Breezy kernel 2.6.12-10-386
modules loaded ieee1394, ohci1394,sbp2 ...

Now what can I do to help to debug this, as there isn't even a panic dump to use?

Georges

---

### Post by sshapiro63 on 2006-03-20
I have problems with firewire disks when using them in a mirror (RAID 1). I can create/mount the /dev/md0 device and it works great. However, if I unmount /dev/md0 and try to mount it again the entire system locks up!

So, it you want to bring Ubuntu down hard, just use firewire!

---

