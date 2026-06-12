---
title: "How Do I Share USB Mount"
date: 2006-02-02
forum: Desktop Environments
---

### Post by mpierce on 2006-02-02
I've got a usb hard drive (/dev/sdb1). 
It currently mounts on /media/lacie.
I've tried umounting and mount on /lacie without success.

I want to share this drive across network with WIN machines.

I've put this in /etc/exports and neither works:
/media/lacie 192.168.1.0/24(rw,sync,no_root_squash) or tried
/lacie 192.168.1.0/24(rw,sync,no_root_squash)

I of course, restart /etc/init.d/nfs-kernel-server restart.

The win machines cannot access driver as path is not found.
\\192.168.1.10\lacie or
\\192.168.1.10\media\lacie

Now they find all the other paths and I can't figure out the problem.
Can I share a usb hard drive across network? If so, how?

---

### Post by gruepig on 2006-02-02
I'm don't know much about Windows, but does Windows have a native NFS client?  I would expect it just uses SMB/CIFS, so you'd either need (1) an NFS client on Windows or (2) to install/configure samba on the Ubuntu side so Windows can access the drive via SMB.

(Numerous docs describe samba configure and configuration of samba accounts, or you can ask in the fora/ums.)

---

### Post by mpierce on 2006-02-04
Forgot to mention that I had configured samba.
Didn't work. It seems that usb/ip has only been enabled in the kernel 2.6.15 and that's the problem. Ubuntu doesn't have a kernel release for this as yet. I can make it work via by linking the drive like this: 
   ln -s /media/sda1 /home/mpierce/usb

---

