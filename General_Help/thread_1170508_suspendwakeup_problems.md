---
title: "suspend/wakeup problems"
date: 2009-05-26
forum: General Help
---

### Post by feh on 2009-05-26
Hi folks.

I think this is actually the case for all variants, but my specific case is kubuntu:

I've got a new install of Kubuntu 9.04 on an ASUS M3N78-VM motherboard, and I can't get the machine to suspend/wake properly.

This is a desktop system - I've installed several power management packages, but none of them work as desired. What I want:

- suspend to RAM (I believe this is state S3), where the fans, CPUs and drives shut down, and the machine wakes up for either a myth recording, or from a key press or mouse event

In other words, not hibernate, but a very low power state where the machine is usable within a few seconds after waking.

To answer some initial questions you may have:

[LIST]
[*]acpid is running
[*]S3 is supported in the BIOS
[*]when I suspend now (either pm_suspend, kpowersave, whatever), the screen goes black, but the fans don't stop, and there's no way to get the machine to respond to any input at this point I have to reset it
[/LIST]

However, I have found that the /etc/acpi/sleep.sh command actually is able to put my machine to sleep (suspend to ram). If I run that command without arguments, nothing happens, but if I use the "force" argument, the machine does suspend.

The problem is that it doesn't resume properly. It tries to wake up, but it spews a bunch of error messages regarding my root filesystem, and then unmounts it, requiring a reset of the machine.

I've done some googling, and I'm wondering if this is an XFS problem. Are any other folks using XFS and are able to get their machine to suspend/wake?

Thanks!

---

### Post by ruben106 on 2009-06-08
I just followed this link and .....it worked for me, so simple...
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462)

---

### Post by feh on 2009-06-08
> **ruben106 said:**
> I just followed this link and .....it worked for me, so simple...
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462)

Thanks. I found that page also, and it does allow me to suspend/wake. My new problem - I can only go through the suspend/wake cycle once. On subsequent suspend attempts, the machine wakes immediately.

:sad:

---

### Post by feh on 2009-10-23
I'm bumping this thread in the hope that folks w/ M3N78 boards will let me know if suspend functionality has improved over the last 4 months, or hopefully, has been greatly enhanced for version 9.10.

I ended up running Windows 7 RC, and I'd really like to go back to linux.

Thanks!

---

### Post by mageus on 2009-11-05
Similar problem.

- ASUS M3N78-VM
- Athlon X4 620 (Phenom-ish)
- Ubuntu 9.04 x32
- SATA HDs & DVD
- NV 9800GT

Suspended fine, but when I resumed I just got a bliking '-' and had to manually power down.

The kernel option pci=nomsi worked, and shutdown/resume worked a couple times in a row.

I had installed 9.10 x64 on another partition prior to reading this post.  It does what you describe - suspend/resume works the first time, then it won't suspend (immediately resumes) on subsequent times during the same power up.  This is default behaviour without any kernel option fix.

I'll try the kernel option fix tomorrow on the 9.10 install.  I'll also post if I start having problems again with the 9.04 x32 install.

Feh, a question:
A lot of people on the Win7 forums are having problem with the onboard video, and also SPDIF working after resume.  Are you using the on-board video or a grafix card?  I'm running off my 9800GT.

---

### Post by feh on 2009-11-05
> **mageus said:**
> Similar problem.

- ASUS M3N78-VM
- Athlon X4 620 (Phenom-ish)
- Ubuntu 9.04 x32
- SATA HDs & DVD
- NV 9800GT

Suspended fine, but when I resumed I just got a bliking '-' and had to manually power down.

The kernel option pci=nomsi worked, and shutdown/resume worked a couple times in a row.

I had installed 9.10 x64 on another partition prior to reading this post.  It does what you describe - suspend/resume works the first time, then it won't suspend (immediately resumes) on subsequent times during the same power up.  This is default behaviour without any kernel option fix.

I'll try the kernel option fix tomorrow on the 9.10 install.  I'll also post if I start having problems again with the 9.04 x32 install.

I have a little more info regarding this problem now:

This behavior seems to be caused by the nvidia driver. After I did a fresh install of 9.10, suspend/resume worked fine, even repeatedly. After I installed the nvidia video driver, I started getting the same behavior I saw in 9.04 - I can suspend/resume once, but subsequent suspend attempts fail; the machine wakes immediately.

> Feh, a question:
A lot of people on the Win7 forums are having problem with the onboard video, and also SPDIF working after resume.  Are you using the on-board video or a grafix card?  I'm running off my 9800GT.

I was running the 7100 RC (maybe the 6100 RC? I can't remember any more), using the onboard 8200. I was using HDMI for audio and video, so I can't speak to any SPDIF issues.

---

### Post by mageus on 2009-11-09
The kernel option fix works for me on 9.10 x32.

Feh, which NV driver version are you running?  I use the ones at [www.avenard.org](www.avenard.org).  He compiles the latest driver and places it into a repository.  I use it because it enables VDPAU.

Try his driver.  If it fixes the problem, then you know it's the old driver.  If it doesn't fix the problem, then it's the onboard video hardware.

---

### Post by feh on 2009-11-09
> **mageus said:**
> The kernel option fix works for me on 9.10 x32.

Feh, which NV driver version are you running?  I use the ones at [www.avenard.org](www.avenard.org).  He compiles the latest driver and places it into a repository.  I use it because it enables VDPAU.

Try his driver.  If it fixes the problem, then you know it's the old driver.  If it doesn't fix the problem, then it's the onboard video hardware.

I'll check it out. Thanks.

---

### Post by browneej on 2010-01-22
Don't know why this works if the problem is the nvidia driver, but I found [[COLOR="Blue"]_this_[/COLOR]]("http://www.xpmediacentre.com.au/community/mythtv-combined-front-backend/41202-mythbuntu-frontend-build-xbmc-mythtv-suspend-resume-remote.html") solution to the one-time-only suspend/hibernate:

> I have recently started having trouble keeping the thing asleep (ie it wakes up immediately after suspending). This seems to have solved it (on both Asrock and Zotac setup). If you are using legacy GRUB, add

Code:
usbcore.autosuspend=-1

to the end of the kernel line in /boot/grub/menu.lst. If you are using GRUB2, then it is a tad more complicated. You need to add it to the option GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, ie

Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"

and update GRUB:

Code:
$ sudo update-grub

Now it seems to work for me.  I get a white screen upon restore, but I hit enter and I get the lock/login screen.

---

### Post by servicetech on 2010-04-13
I too am affected by this bug, machine will suspend once then immediately wakes the 2nd time I try to suspend. Works fine with Windows7 RTM. Running 10.04 beta 2 so it's still not been fixed.

---

### Post by clconway on 2010-05-27
Browneej, This solved the problem for me. This has been bugging me for six months, at least. Thanks!

---

