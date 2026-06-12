---
title: "AMD 7900XT - driver or card issues?"
date: 2023-08-02
forum: Gaming &amp; Leisure
---

### Post by jakebasile on 2023-08-02
Hello, I'm a rather new user of Linux on the desktop / for gaming, and I am lost as to what has happened or how to fix it.

I have a new PC with an AMD R9 7900X3D, an AMD RX 7900XT, and I am running Ubuntu 23.04. `apt` is fully updated, and I don't recall installing anything recently. I played a game last night for hours without any issue. I shut down my PC and went to bed. This afternoon, I got back and found that it hadn't truly shut off, which happens occasionally. I held power to shut it off, and then restarted it as usual. From here, I've been unable to get back to a fully working system with my GPU enabled.

First, I wasn't able to boot at all. It would stop in a boot sequence with the usual output about some ACPI issues, and then the `fsck` output from my sole SSD. Nothing would happen. I booted into a live USB (safe mode) and ran `boot-repair`, which let me get to a GRUB screen and boot into recovery mode. I also ran `fsck` on my disk and it found no errors. In recovery mode, I attempted the following, followed by reboots into "normal" mode, all with no luck getting back GPU acceleration:

- Installed latest stable MESA
- Installed latest unstable MESA
- Installed 6.2.0-24-generic kernel

I'm back to the standard 6.2.0-26 now, and I don't know what else to do. I am able to boot into my system with this kernel, but my video is software accelerated. I am happy to provide any further information or logs, but I don't really know where to start - my experience with Linux is using it to run servers, not games. I'd very much appreciate any help with this. Is my card dead? is it my installation? How can I find out more information?

---

### Post by jakebasile on 2023-08-02
I found some more information. At some point in my flailing, I tried to install the proprietary AMD drivers and these blacklisted the `amdgpu` module. That is what allows me to boot, though obviously that is also why I do not have my GPU enabled. Removing the blacklist for amdgpu causes my boot process to hang right after displaying the fsck output from my SSD. It then gives me a blinking underline cursor that I cannot type at and I am unable to get past.

---

### Post by QIII on 2023-08-03
Why did you try to install the AMD driver?  amdgpu is the driver needed, that is the AMD driver, and the module is used when the OS is installed if the card is supported.   

Do you mean you tried to install the AMDGPU-PRO overlay?

---

### Post by jakebasile on 2023-08-03
I installed the deb from AMD's site [here]("https://www.amd.com/en/support/linux-drivers"), after only being able to boot into recovery mode without any graphics module activated - I thought it might help. It didn't! I've since uninstalled it and unblacklisted the amdgpu module but that brings me back to being unable to get past boot. Only with the amdgpu module blacklisted can I get to a working machine. I *am* able to boot into a 23.04 live USB with full graphics though, so I think the problem lies somewhere in my filesystem, I just don't know where or how to find out where.

Do you know of a way I can gather information on why a boot might hang in the very initial stages, right after the `fsck` output as in this image? I apologize for not being able to post the actual text and only a photo of my screen, since I don't know where to find this output.

[IMG]https://i.imgur.com/ODEwGye.png[/IMG]

---

### Post by jakebasile on 2023-08-03
reading `journalctl` helped me find what I think is the actual error, though searching key text from it hasn't yielded much help other than a couple other people having the same issue, [some of whom say it is fixed with much older kernel versions]("https://gitlab.freedesktop.org/drm/amd/-/issues/2079") than what I am using.

```

Aug 02 17:12:01 monolith kernel: amdgpu 0000:03:00.0: amdgpu: SMU: I'm not done with your previous command: SMN_C2PMSG_66:0x00000006 SMN_C2PMSG_82:0x00000000
Aug 02 17:12:01 monolith kernel: amdgpu 0000:03:00.0: amdgpu: Failed to enable requested dpm features!
Aug 02 17:12:01 monolith kernel: amdgpu 0000:03:00.0: amdgpu: Failed to setup smc hw!
Aug 02 17:12:01 monolith kernel: [drm:amdgpu_device_ip_init [amdgpu]] *ERROR* hw_init of IP block <smu> failed -62
Aug 02 17:12:01 monolith kernel: amdgpu 0000:03:00.0: amdgpu: amdgpu_device_ip_init failed
Aug 02 17:12:01 monolith kernel: amdgpu 0000:03:00.0: amdgpu: Fatal error during GPU init

```

---

### Post by selective-panic on 2023-08-03
hi, sorry about my english

I recently found my similairly spec'ed PC to not be able to display drive password prompt after grub menu.
Reconnecting my monitor to iGPU allowed me to enter the drive password but (X11) login manager did not show up.
Rebooting with monitor connected to iGPU allowed me to log in and investigate.

```
Kubuntu 23.04 (updated)
6.2.0-26-generic
```

```
$ lspci -v | grep -EA15 "03:00.0 VGA compatible controller"
```
The following line was missing (in the section of 03:00.0):
'Kernel driver in use: amdgpu'

[skipping detailed info]

After some time I narrowed my problem to:

```
$ apt show linux-firmware
Package: linux-firmware
Version: 20230323.gitbcdcfbcf-0ubuntu1.4
```

because after downgrading it with the use of ```
$ sudo synaptic
```
```
$ apt policy linux-firmware
linux-firmware:
  Installed: 20230323.gitbcdcfbcf-0ubuntu1.2
  Candidate: 20230323.gitbcdcfbcf-0ubuntu1.4
```

I was able to boot and resume normal operation (need to digg what exacly I lost in terms of firmware security updates)
I'm preparing more detailed baby's first report and I'll post it here and wherever advanced magicians point me to when it's ready.

It does not seem to me that this important 'linux-firmware' package is in phased updates but idk.



[https://packages.ubuntu.com/search?keywords=linux-firmware](https://packages.ubuntu.com/search?keywords=linux-firmware)
lists
```
mantic (misc): Firmware for Linux kernel drivers
20230731.git07f05b0c-0ubuntu1
```

which looks newer that any of those:
```
20230323.gitbcdcfbcf-0ubuntu1.2
20230323.gitbcdcfbcf-0ubuntu1.4
```

so maybe they know there is a problem and fix is waiting for validation.

---

### Post by selective-panic on 2023-08-03
Let me mention those:
[https://ubuntuforums.org/showthread.php?t=2489556](https://ubuntuforums.org/showthread.php?t=2489556) [my baby's first post with aditional info about my baby's first investigation]
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396)
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029434](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029434)

I'll try to boot with this:
[https://launchpad.net/ubuntu/+source/linux-firmware/20230323.gitbcdcfbcf-0ubuntu1.3/+build/26397687](https://launchpad.net/ubuntu/+source/linux-firmware/20230323.gitbcdcfbcf-0ubuntu1.3/+build/26397687)

as mentioned here:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396/comments/7)

---

### Post by jakebasile on 2023-08-03
Thanks for the reply selective-panic. The linked errors do look similar, and when I get home I will try to roll back the offending package to see if that solves my problem.

---

### Post by jakebasile on 2023-08-03
Thanks again selective-panic, this was the cause of my issue. Running the following fixed it (for now) and should mark the package as pinned until the bugs are resolved.

```

sudo apt update
sudo apt upgrade
sudo apt install linux-firmware=20230323.gitbcdcfbcf-0ubuntu1.2
sudo apt-mark hold linux-firmware


```

---

### Post by selective-panic on 2023-08-05
I just deleted -proposed from my system, reverted to 1.2, updated to 1.5 from -updates and rebooted.

Looks like it may be safe to unhold the package and update.

perf looks normal:
```
$ DRI_PRIME=0 vblank_mode=0 glxgears
```

```
$ apt policy linux-firmware
linux-firmware:
  Installed: 20230323.gitbcdcfbcf-0ubuntu1.5
  Candidate: 20230323.gitbcdcfbcf-0ubuntu1.5
  Version table:
 *** 20230323.gitbcdcfbcf-0ubuntu1.5 500
        500 http://gb.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
```

edit (because new post got folded to a new page I copied it here to minimise the chance You miss it and encounter problems):

Now if I think about it, if You use AMD drivers from their website,
they may expect the newer firmware that was in 1.4 but got reverted in 1.5.

New kernel releases this week as mentioned here:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396/comments/33](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396/comments/33)
and the new firmware needs new kernel.

So, maybe wait, there may be no point in testing AMD drivers with software setup that is going to go away in few days.

---

### Post by selective-panic on 2023-08-05
Now if I think about it, if You use AMD drivers from their website,
they may expect the newer firmware that was in 1.4 but got reverted in 1.5.

New kernel releases this week as mentioned here:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396/comments/33](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2029396/comments/33)
and the new firmware needs new kernel.

So, maybe wait, there may be no point in testing AMD drivers with software setup that is going to go away in few days.

---

### Post by jakebasile on 2023-08-07
I've been following along with the various bugs mentioned, and it seems to be in a state of flux. I think I'm going to hold kernel updates as well and just give this some time to settle, as things appear to work on my system with 6.2.0-26 and firmware 1.2. 

Thanks for the follow up!

---

### Post by xlmnxp on 2024-02-09
Hello
I'm facing same issue and it don't happen often (I can boot after 10-20 try),
the issue happen too for Fedora (kernel 6.7) and Manjaro

my distro is Kubuntu 23.10 and kernel version is 6.5 and I tried 6.8 manually (same issue)

Is there way to resolve the issue?

CPU: Ryzen 9 7950X
GPU: Radeon RX 7900 XTX (Founder Edition from Sapphire)
Motherboard: Gigabyte B650M GAMING X AX 

Error message in dmesg logs:
```

amdgpu: Failed to setup smc hw!
 *ERROR* hw_init of IP block <smu> failed -62

```

I opened bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2052840](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/2052840)

---

