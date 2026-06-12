---
title: "Ubuntu under Windows"
date: 2008-09-16
forum: Desktop Environments
---

### Post by gweir on 2008-09-16
Hi,

I am new to Ubuntu and have installed 8.04.1 under Windows XP rather than creating a separate partition or completely replacing Windows.

I was expecting Ubuntu to run as an emulation under Windows but it is much better than that and seems to boot as a separate system, albeit residing within the Windows NTFS file system.

My question is -

Since this appears to be a proper Ubuntu system boot without Windows does this mean that the security setup is the same as if Ubuntu had been installed as the only operating system on the computer ? 

Thanks for your help.

---

### Post by jdackle on 2008-09-16
Don't know if I can help but will try. But do take this with a considerable amount of salt - I wasn't even aware Ubuntu could be installed that way! (some vague recollection on that but... :-D )

Anyways, my 2 cents in 2 points:

1. I believe the fact Windows and Linux share the same disk on different partition does not significantly diminish Linux's security. AFAIK, Windows cannot write or even read any filesystem-format native or commonly used by Linux internally (e.g. ext2 and ext3), thus it itslef will not mess with a Linux partition (although, you don't really know wether Micro$oft has enabled read/write access to Linux filesystems as you don't have access to their source-code, do you?).
But on the other hand, the "fact" Windows itself doesn't know how to mess with a Linux partition does not mean some kind of software running on it doesn't (one example is ext2fs, a handy program to access your ext2/3 partition from inside Windows). Thus it seems technically possible some virus might infect Windows and then from there on access your Linux partition... But the targeting of viruses to Linux is so insignificant it does not seem very likely to me. But then again, what do I know? :-P

2. Given what I said above, Ubuntu being in a NTFS partition makes all its files much more accessible to any sort of malware, or even more so someone gaining "live" access to your disk, physically or through some network.
Regarding Linux executables, the intruder (automated or not) would probably not know how to infect one. however, they would be very easily deleted...
Also any file-formats know to the Windows world (documents, images, etc) would be vulnerable.

There ya go, my 2 cents worth!... :mrgreen:

---

### Post by gnuvistawouldbecool on 2008-09-16
> **gweir said:**
> Hi,

I am new to Ubuntu and have installed 8.04.1 under Windows XP rather than creating a separate partition or completely replacing Windows.

I was expecting Ubuntu to run as an emulation under Windows but it is much better than that and seems to boot as a separate system, albeit residing within the Windows NTFS file system.

My question is -

Since this appears to be a proper Ubuntu system boot without Windows does this mean that the security setup is the same as if Ubuntu had been installed as the only operating system on the computer ? 

Thanks for your help.

So, you have installed Ubuntu in a Windows partition, using Wubi, from the sounds of it.  As such, it is basically running in a virtual disc *inside* the windows partition itself.  Think of it as a spot of ext3 format inside an ntfs disc.  

AFAIK you can't access the virtual disc from XP, though it can get fragmented since it is a file in Windows.  Unless you have a system that can read the virtual disc, (presumably like the kernel itself does) then it is secure.  A virus may be able to infect the virtual disc file itself, but unless the drive is actually opened, it would only infect it for the use of windows itself.

---

### Post by gweir on 2008-09-16
> **gnuvistawouldbecool said:**
> So, you have installed Ubuntu in a Windows partition, using Wubi, from the sounds of it.  As such, it is basically running in a virtual disc *inside* the windows partition itself.  Think of it as a spot of ext3 format inside an ntfs disc.  

AFAIK you can't access the virtual disc from XP, though it can get fragmented since it is a file in Windows.  Unless you have a system that can read the virtual disc, (presumably like the kernel itself does) then it is secure.  A virus may be able to infect the virtual disc file itself, but unless the drive is actually opened, it would only infect it for the use of windows itself.
Hi,

Yes, that's exactly how it is - installing under Windows was one of the options on the distribution disk - I didn't know it was using Wubi but that does seem to be the case.

Ubuntu exists in a folder on the C drive and can be seen from Windows, but gets booted as a stand-alone system.
 
Many thanks for the advice.

---

