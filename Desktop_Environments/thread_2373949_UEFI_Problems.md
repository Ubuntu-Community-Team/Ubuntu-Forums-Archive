---
title: "UEFI Problems"
date: 2017-10-11
forum: Desktop Environments
---

### Post by Geoff_Lane on 2017-10-11
Folks,

Just under a year ago I purchased a Toshiba Satellite laptop with Windows 10 installed.

Rarely use Windows but to protect warranty I installed Ubuntu 16:04 on a small neat USB stick using legacy boot. Now at the time I thought the GRUB boot was all installed to the USB stick and it boots fine BUT if I revert to EUFI it boots into >grub

If I use the normal USB boot I get a normal grub menu, if I opt for the Windows Recovery option I get message of a problem with the boot and to install the CD to repair the problem. I never got a disk.

Now whilst I can still run Ubuntu fine I'd like to have Windows available so to my question;

Is EUFI a Microsoft system because all the repair methods I see appear to be using a Windows DVD. My EUFI boot partition shows fine in gparted, and within the EFI folder there is as follows;

Boot
Microsoft
ubuntu

Any pointers appreciated.

Geffers

---

### Post by jeremy31 on 2017-10-11
I think you have to use Windows to make a recovery disk to make any use of the windows recovery partition.  If you want windows to load see if one of the grub options is windows loader

---

### Post by Geoff_Lane on 2017-10-11
> **jeremy31 said:**
> I think you have to use Windows to make a recovery disk to make any use of the windows recovery partition.  If you want windows to load see if one of the grub options is windows loader

Jeremy,

Thank you for quick reply.

If I set computer to boot EUFI then I end up with grub command line.

If I boot by the old method I get the normal Grub Menu and one option is as follows;

Windows Recovery Environment

If I select that I am invited to insert the Windows DVD which I haven't got.  :(

Geffers

---

### Post by Geoff_Lane on 2017-10-11
All sorted.

I used Ubuntu command line to mount the Windows EFI partition. There were three folders inside, Boot, Microsoft and ubuntu.

The latter should not have been there so I used sudo to remove it.

Rebooted and Windows10 appeared.

Now back in Ubuntu but at least Windows an option.

I'll show this thread as solved.

Geffers

---

