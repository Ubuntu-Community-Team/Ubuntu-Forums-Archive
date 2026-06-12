---
title: "Internet nolonger starts when booting."
date: 2005-12-30
forum: Desktop Environments
---

### Post by encompass on 2005-12-30
I nolonger have internet when I reboot.  I need to dhclient eth0 before I get a connect.  I didn't think I changes the settings.  Any ideas?

---

### Post by dcstar on 2005-12-30
[QUOTE=encompass]I nolonger have internet when I reboot.  I need to dhclient eth0 before I get a connect.  I didn't think I changes the settings.  Any ideas?[/QUOTE]
Edit /etc/default/bootlogd to have: BOOTLOGD_ENABLE=Yes

Then after a reboot you should be able to see in Application-System Tools-System Log /var/log/boot any error message related to the network.

That should help in looking for the problem/solution.

---

### Post by encompass on 2006-01-01
I edited the file to say 'Yes' using
> sudo nano /etc/default/bootlogd
rebooted... and I don't see the /var/bog/boot
so I added the log my self after taking a look with nano first.

Well we got a garbles mess, but for the most part... this...
>   Sun
  Sun Jan  1 07:03:53 2006: ^[[122G[ ok ]g disc parameters...       ^[[128G 
  Sun Jan  1 07:03:53 2006:  * Checking root file system...       ^[[128G /: clean, 130673/549440 files, 782845/1098436 blocks
  Sun Jan  1 07:03:53 2006: ^[[122G[ ok ]
  Sun Jan  1 07:03:53 2006: ^[[122G[ ok ]ng modules...       ^[[128G 
  Sun Jan  1 07:03:53 2006: ^[[122G[ ok ]p ifupdown...       ^[[128G 
  Sun Jan  1 07:03:54 2006: ^[[122G[ ok ]g module dependencies...       ^[[128G 
  Sun Jan  1 07:03:57 2006: ^[[122G[ ok ]dules...       ^[[128G 
  Sun Jan  1 07:03:58 2006: ^[[122G[ ok ]e system clock...       ^[[128G 
  Sun Jan  1 07:04:01 2006:  * Checking all file systems...       ^[[128G /home: clean, 24550/647680 files, 1214511/1293232 blocks (check in 5 mounts)
  Sun Jan  1 07:04:01 2006: ^[[122G[ ok ]
  Sun Jan  1 07:04:01 2006:  * Mounting local filesystems...       ^[[128G /dev/hda3 on /home type ext3 (rw)
  Sun Jan  1 07:04:01 2006: ^[[122G[ ok ]
  Sun Jan  1 07:04:02 2006: ^[[122G[ ok ] networking...       ^[[128G 
  Sun Jan  1 07:04:02 2006: ^[[122G[ ok ]sktop files...       ^[[128G 
  Sun Jan  1 07:04:03 2006: ^[[122G[ ok ]otplug subsystem...       ^[[128G 
  Sun Jan  1 07:04:16 2006: ^[[122G[ ok ]g network interfaces...       ^[[128G 
  Sun Jan  1 07:04:16 2006: ^[[122G[ ok ]r network interface to come up...       ^[[128G 
  Sun Jan  1 07:04:17 2006: ^[[122G[ ok ] ALSA...       ^[[128G 
  Sun Jan  1 07:04:17 2006: ^[[122G[ ok ]e system clock...       ^[[128G 
  Sun Jan  1 07:04:18 2006:  * Synchronizing clock to ntp.ubuntulinux.org...       ^[[128G Error : Temporary failure in name resolution
  Sun Jan  1 07:04:18 2006: ^[[122G[^[[31mfail^[[39;49m]
  Sun Jan  1 07:04:18 2006: ^[[122G[ ok ]ng random number generator...       ^[[128G 
  Sun Jan  1 07:04:18 2006:  * Entering runlevel: 2
  Sun Jan  1 07:04:19 2006: ^[[122G[ ok ]PI modules...       ^[[128G 
  Sun Jan  1 07:04:20 2006: ^[[122G[ ok ]CPI services...       ^[[128G 
  Sun Jan  1 07:04:20 2006: ^[[122G[ ok ]ystem log daemon...       ^[[128G 
  Sun Jan  1 07:04:21 2006: ^[[122G[ ok ]ernel log daemon...       ^[[128G 
  Sun Jan  1 07:04:21 2006: ^[[122G[ ok ]ystem message bus...       ^[[128G 
  Sun Jan  1 07:04:22 2006: ^[[122G[ ok ]ardware abstraction layer:        ^[[128G 
  Sun Jan  1 07:04:24 2006: ^[[122G[ ok ]g up general console font...       ^[[128G 
  Sun Jan  1 07:04:25 2006: ^[[122G[ ok ]n^[D^[[1F^[[1X^[%G^[[9;30]^[[14;30] * Starting GNOME Display Manager...       ^[[128G 
  Sun Jan  1 07:04:28 2006: ^[[122G[ ok ]CMCIA services...       ^[[128G 
  Sun Jan  1 07:04:32 2006:  * Starting powernowd...        ^[[128G  * CPU frequency scaling not supported
  Sun Jan  1 07:04:32 2006: ^[[122G[ ok ]
  Sun Jan  1 07:04:32 2006: ^[[122G[ ok ]penBSD Secure Shell server...       ^[[128G 
  Sun Jan  1 07:04:33 2006: Starting internet superserver: xinetd.
  Sun Jan  1 07:04:33 2006: Saved ALSA mixer settings detected; aumix will not touch mixer.
  Sun Jan  1 07:04:33 2006: ^[[122G[ ok ] X server socket directory...       ^[[128G 
  Sun Jan  1 07:04:33 2006: ^[[122G[ ok ] ICE socket directory...       ^[[128G 
  Sun Jan  1 07:04:34 2006: ^[[122G[ ok ]nac(h)ronistic cron: anacron       ^[[128G 
  Sun Jan  1 07:04:34 2006: ^[[122G[ ok ]eferred execution scheduler...       ^[[128G 
  Sun Jan  1 07:04:34 2006: ^[[122G[ ok ]eriodic command scheduler...       ^[[128G 
  Sun Jan  1 07:04:34 2006: ^[[122G[ ok ]dditional executable binary formats...        ^[[128G 
  Sun Jan  1 07:04:35 2006: ^[[122G[ ok ]attery state...       ^[[128G 
  Sun Jan  1 07:04:36 2006: 
I don't see any errors, in this output.  Perhaps you do?

---

### Post by encompass on 2006-01-02
UPDATE:
I saw by chance the bootlogd loading at boot and it said it [failed]
any ideas?

---

### Post by dcstar on 2006-01-02
[QUOTE=encompass]UPDATE:
I saw by chance the bootlogd loading at boot and it said it [failed]
any ideas?[/QUOTE]
That's a known bug in the current bootlogd, ignore it as it actually works.

Your boot log has no obvious error as far as starting the Ethernet card goes, so it may well be a configuration issue.

What is the output of **ifconfig** and **netstat -rn** straight after booting up?

---

