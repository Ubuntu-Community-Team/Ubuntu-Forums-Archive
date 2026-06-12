---
title: "Grub won't boot (new hardware was added)"
date: 2009-06-17
forum: General Help
---

### Post by pattersondm85 on 2009-06-17
Hello,

I have been running MythBuntu for about 7 months now and have a couple front ends up and running. However, I ran into a problem I am not sure how to resolve.

My setup is as follows.
x86 CPU
2 IDE hard drives on the same ribbon

Everything worked just fine with Ubuntu 8.04 installed. Until, the other day my hard drive(s) were starting to fill up so got new 1TB SATA drive.  My media server doesn't have SATA (it is older) so my roommate gave me his old PCI to SATA (model PNY p-dsa150-pci-rf).

So fast forward and new drive and PCI to SATA controller is installed.  I boot up machine and it detects my two IDE HDDs and the SATA controller and the 1TB drive.  Then it get to the point where it says Loading Grub 1.5 and just stops. I was expecting to see the press esc for boot menu and the 3..2..1.. count down. but nope, nothing.

I removed SATA cable from 1TB HDD and ubuntu booted just fine. I threw in a bootable knoppix distro and knoppix saw the drive and I formatted it as ext3 while I had the chance.

So what might be causing my Grub to fail loading Ubuntu? I am not dual booting either.

Let me know if you need more information about my setup. Since, I am unable to add any more media or record any more shows currently. Thank, you in advance for any help you are able to lend.

Devin

---

### Post by synapsys on 2009-06-17
It's probably seeing the sata hard drive as the primary hard drive and trying to boot from it. I would boot the system, then plug in the hard drive, then map it with fstab, then reboot.

---

### Post by pattersondm85 on 2009-06-17
I had the same thought about the boot order. I just wasn't sure how to correct it. I am still new linux, I give that a try when i get home from work.

Thanks

---

### Post by Hobgoblin on 2009-06-17
I would check the boot order in the BIOS.  If the BIOS doesn't see the SATA controller/drive then you may need to reinstall GRUB.

---

### Post by pattersondm85 on 2009-06-17
> **Hobgoblin said:**
> I would check the boot order in the BIOS.  If the BIOS doesn't see the SATA controller/drive then you may need to reinstall GRUB.

I have look at BIOS up and down thinking the same thing but it doesn't seen the SATA Controller or drive.

---

### Post by synapsys on 2009-06-17
> **pattersondm85 said:**
> Hello,
 I boot up machine and it detects my two IDE HDDs and the SATA controller and the 1TB drive. 

...

---

### Post by pattersondm85 on 2009-06-17
> **synapsys said:**
> ...

BIOS detects the 2 IDE harddrive, and the SATA controller shows the 1 SATA drive. This is all during the boot processes before Grub is loaded.

---

### Post by synapsys on 2009-06-17
If it's detected, it's detected. I had this same problem before when I plugged my eSATA drive in Grub tried to boot from it. I started the system without it, mapped it with fstab, rebooted with it plugged in, then it worked. 

If you are unsure how to edit your fstab just search these forums, it has been covered plenty of times.

---

### Post by pattersondm85 on 2009-06-17
> **synapsys said:**
> If it's detected, it's detected. I had this same problem before when I plugged my eSATA drive in Grub tried to boot from it. I started the system without it, mapped it with fstab, rebooted with it plugged in, then it worked. 

If you are unsure how to edit your fstab just search these forums, it has been covered plenty of times.


I have edited my fstab numerous time but never for a drive. Just for mapping smb shares from other serves in the house. I will look up some of the commands again.

Keep the ideas coming, since I will run down the list tonight.
Thanks

---

### Post by pattersondm85 on 2009-06-18
So here is what I tried tonight. 

1) With drive disconnected booted up to OS. Plugged drive in and drive loaded. was able to see drive. Rebooted with drive still plugged in. Still stopped right when it was waiting to load Grub.

2) removed drive, booted into OS. edited my /etc/fstab file for the drive. Made sure the drive was mapped to a real location. Rebooted and still stopped at the loading Grub screen.

So what do people purpose what I should do next?

---

### Post by pattersondm85 on 2009-06-20
Ok some more news.  I reinstalled Grub with no sucess, I used this guide for reinstalling grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)).

I still see
```
GRUB Loading stage1.5


GRUB loading, please wait...
```

But as soon and I disconnect the SATA cable from the harddrive GRUB will load no problem.  Anyone have anymore thoughts on this issue?

Thanks,
Devin

---

### Post by pattersondm85 on 2009-06-20
> **synapsys said:**
> It's probably seeing the sata hard drive as the primary hard drive and trying to boot from it. I would boot the system, then plug in the hard drive, then map it with fstab, then reboot.

Ok like side I had tried this and it didn't work but I did get an error message when I plugged the SATA drive in once ubuntu was loaded.

The error was
```
Failed to mount "1TB Volume".
org.freedesktop.hal.storage.mount-fixed
auth_admin_keep_always<-- (action, result)

```

If you know what that means please let me know.
Thanks again

---

