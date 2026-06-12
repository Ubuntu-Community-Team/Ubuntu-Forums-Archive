---
title: "VirtualBox's disk passthrough and dual booting"
date: 2008-12-23
forum: General Help
---

### Post by archivator on 2008-12-23
I was recently contemplating the possibility of running an already installed system in virtualbox.

VB provides a mechanism which exposes a host drive to the guest OS as-is. Thus, I could, theoretically, boot my windows OS from Ubuntu. Talk about seamless integration.. 

Question is, has anyone tried this and if so, any hiccups around drivers and such?

---

### Post by ju2wheels on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

In terms of hardware, you Windows install would see your hardware as the VirtualBox virtual hardware adapters when running inside of the VM. I have read that the only issue is the use of guest additions if you are going to still be booting into that OS outside of the VM (which was confirmed again by the post i found above when I googled it).

---

### Post by archivator on 2008-12-24
Thanks for the link!I swear, I did search before I posted! :oops:

I was afraid of something like that guest additions catch.. A guest OS without the additions is tiresome to use and I don't want to sacrifice native booting in Windows (not to mention the fact that I have a SCSI controller that was notoriously difficult to install on Windows, I don't want to go through that again). 

The guest additions are OSS, right? I'll see if I can find the cause of the problem..

---

### Post by ju2wheels on 2008-12-24
I think the ideal and easiest solution to that problem would be the design of secondary application in addition to the guest additions that is able to determine whether or not you are running in a VM or not at Windows boot time and selectively use either the native system drivers or the guest additions drivers. Ive never dabbled much in Windows programming so I dont know how feasible that is.

---

