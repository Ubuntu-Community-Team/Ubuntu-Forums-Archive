---
title: "Unable to boot after installing Ubuntu"
date: 2005-07-25
forum: Desktop Environments
---

### Post by spencer on 2005-07-25
Hi,

I just installed Ubuntu and now I'm not able to boot into my other linux system which is Fedora. Why is this happening? 

Here is my setup:

I have two interal hard drives, one 10 GB the other 20 GB. I have Fedora on the 20 GB(hda1) drive and XP on the 10 GB(hdb1 drive with 5 Gigs(hdb2) assigned for Ubuntu on the 10 GB drive. Swap is on hda2. 

So, I install Ubuntu on the 5 GB(hdb2) drive and then install grub to a floppy instead of the mbr. I can boot into Ubuntu but not Fedora or XP. I have a boot floppy for XP so I can still get into XP with the floppy or if I change the boot sequence in the bios. It's Fedora that I'm not able to get into. Where have I gone wrong?

If I delete Ubuntu I have access to Fedora again.

Some of the errors I get when trying to boot fedora are '/etc/rc.sysinit: line 927:' and '/var/log/dmesg: Read-only file system' I have no idea what that means. It just hangs there for a few minutes and then the boot continues to the next message:

'I could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart gdm when the problem is corrected.'

 I don't know what that means either.

How can I fix this? 

Thanks,

-spencer

---

### Post by majikstreet on 2005-07-25
[QUOTE=spencer]Hi,

I just installed Ubuntu and now I'm not able to boot into my other linux system which is Fedora. Why is this happening? 

Here is my setup:

I have two interal hard drives, one 10 GB the other 20 GB. I have Fedora on the 20 GB(hda1) drive and XP on the 10 GB(hdb1 drive with 5 Gigs(hdb2) assigned for Ubuntu on the 10 GB drive. Swap is on hda2. 

So, I install Ubuntu on the 5 GB(hdb2) drive and then install grub to a floppy instead of the mbr. I can boot into Ubuntu but not Fedora or XP. I have a boot floppy for XP so I can still get into XP with the floppy or if I change the boot sequence in the bios. It's Fedora that I'm not able to get into. Where have I gone wrong?

If I delete Ubuntu I have access to Fedora again.

Some of the errors I get when trying to boot fedora are '/etc/rc.sysinit: line 927:' and '/var/log/dmesg: Read-only file system' I have no idea what that means. It just hangs there for a few minutes and then the boot continues to the next message:

'I could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart gdm when the problem is corrected.'

 I don't know what that means either.

How can I fix this? 

Thanks,

-spencer[/QUOTE]
 I'm not sure but it seems like grub isn't configured for Fedora right.

I have no idea how to do that-- just giving some input.

---

### Post by spencer on 2005-07-26
Thanks for your reply.

 I searched all day and found nothing regarding this issue. I think you're right. It looks to be a grub problem because of the error 'I could not start the X server due to some internal error.'

The question is how to get X backup and running.

I'll keep looking into it and share the solution as soon as I find it. When I delete Ubuntu I can get back in Fedora, no problmes. I don't want to delete Ubuntu though. 

If anyone can help, please do.

-spencer

---

