---
title: "VMWare woes"
date: 2006-08-16
forum: Desktop Environments
---

### Post by sbaker33 on 2006-08-16
I seem to be having a lot of trouble with the vmware files (VMDK) on Ubuntu.  Twice already I have had vmware lock up and if I was able to recover it appeared to be currupted files on the HDD.  Once the problems were so bad I ended up reinstalling Ubuntu completely.  The install I have now has been running for a couple of weeks with few problems but I fear I am about to have problems again.

I was copying a vmware image (folder with .vmdk and config files) to a windows file server and the copy crashed on one of the .vmdks  I tried copying the file locally on the HDD and it failed in about the same place.  I tried copying the file again after rebooting thinking something had a lock on the file but no difference.  I tried compressing the files which worked but once decompressed on the target machine the file(s) was corrupt.  I tried copying via the command line rather than GUI but no difference.  I receive an error "Input/output error."

The file seems to work fine when I run the VM, at least I haven't received any errors yet.

So, I have two questions:
1) What if anything can I do to recover this file?  I can recreate the work but would prefer not to.
2) Is this a Ubuntu/VMware thing?  or could it be my hardwrae going bad? Any ideas?

---

### Post by pdub on 2006-08-16
What size is the vmdk file?
What is the file system on the Windows computer that you are copying to?
What us the file system type on the Ubuntu machine?

I have vmware workstation 5.5.2 running on a dozen classroom machines (Ubuntu 6.06) and have had no problems. In fact, Ubuntu has been far more stable than my previous Suse 10 install. I did have some problems with a bad NIC driver that cause several vmdk files to become corrupt during copy under Suse 10 though.

---

### Post by sbaker33 on 2006-08-17
> **pdub said:**
> What size is the vmdk file?

The VMDK file is a 1.1 GB Windows XP image created in Workstation 5.5

> **pdub said:**
> What is the file system on the Windows computer that you are copying to?

NTFS, on a Windows 2000 Server; 75 GB drive with 27 GB free however, I can't even copy the file locally on the Linux machine.  

> **pdub said:**
> What us the file system type on the Ubuntu machine? 

ext3 with 8 GB free on a 27 GB drive.  About 8 of this is split between 5 VMWare images (WinXP, WIn2k, Win98, Ubuntu Server 5.10 and Xubuntu 6.06)

> **pdub said:**
> I have vmware workstation 5.5.2 running on a dozen classroom machines (Ubuntu 6.06) and have had no problems. In fact, Ubuntu has been far more stable than my previous Suse 10 install. I did have some problems with a bad NIC driver that cause several vmdk files to become corrupt during copy under Suse 10 though.

hmmmm, how did you determine the bad NIC driver?  Is there any way to test and see if this is a hardware problem with my Dell laptop?  Dell diag utilities, IMHO, are useless.  

Thanks

---

### Post by pdub on 2006-08-17
I was going to ask if you could copy it locally, that is a strange problem.

Not likely a problem with the NIC driver if it happens locally.

Do other large files corrupt when you copy them? Something like a large ISO file. Take an MD5 sum of some large files an try copying them. Then check their MD5 sum after. Try several files. If they corrupt then it's not vmware causing the problem.

**md5sum filename**

---

### Post by sbaker33 on 2006-08-18
I have installed Ubuntu on another laptop and just finished installing VMWare.  I will copy the VMs that are still good to the new machine and begin recreating my work on the one that is not.  I will run for a bit on this machine and see if that changes anything.  

What file system are you running on your machines?  My installation defaulted to ext3, is that what you are using?  Is that the best choice?

---

### Post by pdub on 2006-08-19
I am using reiser on all systems.

---

