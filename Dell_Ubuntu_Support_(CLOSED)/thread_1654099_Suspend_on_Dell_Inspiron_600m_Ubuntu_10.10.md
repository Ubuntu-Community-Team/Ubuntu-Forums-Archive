---
title: "Suspend on Dell Inspiron 600m Ubuntu 10.10"
date: 2010-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lido on 2010-12-27
I've got a 600m and can't seem to get suspend or even hibernate to work. There are a lot of threads about it and some bug reports on launchpad complaining about the problem as well. A few people have claimed on earlier Ubuntu releases that it was possible by disabling acpi and using apm. I believe I've done that, but it doesn't seem to be working for me. Here are the steps I took, please let me know if I missed/munged anything. Thanks.

1)

in /etc/default/grub

I added "apm=on acpi=off" to the GRUB_CMDLINE_LINUX_DEFAULT line.

2)

sudo update-grub

3)

in /etc/modprobe.d/blacklist

I added:

```
shpchp
pciehp
```

4)

in /etc/modules

I added:

```
apm
```

5)

reboot

Now when I select "suspend" from the reboot window, the screen goes black, there's some disk activity, but it never suspends. If I hit the power button it just kills the power (i.e. no shutdown, just instant death).

Hibernate pretty much does the same.

---

### Post by cipherboy_loc on 2010-12-27
What is the output of:
```
sudo fdisk -l
```

```
cat /etc/fstab
```

```
sudo mount
```

The first command shows the disks that you have connected (internal and USB), the second one shows what gets mounted at boot, and the third command shows what is mounted currently. 


Thanks,
Cipherboy

---

### Post by Lido on 2010-12-28
Thanks for the reply. I'm not sure how that info would help unless you're just trying to see that there's a swap partition, but here you go...

[QUOTE=cipherboy_loc;10286248]What is the output of:
sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b4e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9539    76616704   83  Linux
/dev/sda2            9539        9730     1531905    5  Extended
/dev/sda5            9539        9730     1531904   82  Linux swap / Solaris
```

cat /etc/fstab
```
 more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=581a85f2-b72e-4b3f-a4d4-e300deed2407 none            swap    sw              0       0

```

sudo mount
```
lido@lido-Inspiron-600m:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/lido/.Private on /home/lido type ecryptfs (ecryptfs_sig=58d1a6c8ac301dd6,ecryptfs_fnek_sig=ec077e85083e5a54,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/lido/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lido)
```

---

### Post by cipherboy_loc on 2010-12-29
Yeah, I was looking for a swap partition for hibernation. I have a Dell Inspiron 6000, and I had to install pm-utils for it to work:

```

sudo apt-get install pm-utils

```Now, let me make sure that I can hibernate... I was having issues before I installed the pm-utils package, but I think it works now.

EDIT: I can hibernate.
Cipherboy

---

### Post by Lido on 2010-12-29
I've got pm-utils already installed (this is a fresh install so it must go in by default in 10.10).

---

### Post by gesho on 2011-01-01
hibernate works for me no probs out of box, without any changes (600m). suspend in 10.10 is hopeless, it used to work in earlier releases.

---

### Post by Lido on 2011-01-01
> **gesho said:**
> hibernate works for me no probs out of box, without any changes (600m). suspend in 10.10 is hopeless, it used to work in earlier releases.

Thanks. I'll try hibernate again. Two questions, how do you get it out of hibernate? Do you remember which release had suspend working?

---

### Post by cipherboy_loc on 2011-01-02
> **Lido said:**
> Thanks. I'll try hibernate again. Two questions, how do you get it out of hibernate? Do you remember which release had suspend working?

Hibernation is, by definition, saving the state of your machine to disk (hence the need for a Linux Swap partition/file), and powering the device completely off. To 'resume' from hibernation, press the power button. When it resumes, it reads everything back off the disk, and into RAM.



Cipherboy

---

### Post by gesho on 2011-01-02
i believe it was on and off. i believe it worked at some point in 9.xx releases. 

to get out of hibernate, do as if you were powering up in regular way and if you hibernated (rather than shut down) it will resume (rather than boot).

---

### Post by Lido on 2011-01-03
> **gesho said:**
> i believe it was on and off. i believe it worked at some point in 9.xx releases. 

to get out of hibernate, do as if you were powering up in regular way and if you hibernated (rather than shut down) it will resume (rather than boot).

Thanks. How much ram do you have? I'm getting the error messages:

PM: Not enough memory
PM: Error -12 creating hibernation image

from syslog:

```
Jan  3 16:47:11 lido-Inspiron-600m init: anacron main process (2108) killed by TERM signal
Jan  3 16:47:11 lido-Inspiron-600m kernel: [  409.944988] PM: Marking nosave pages: 0000000000002000 - 0000000000010000
Jan  3 16:47:11 lido-Inspiron-600m kernel: [  409.944993] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Jan  3 16:47:11 lido-Inspiron-600m kernel: [  409.944998] PM: Basic memory bitmaps created
Jan  3 16:47:17 lido-Inspiron-600m acpid: client 889[0:0] has disconnected
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  409.945001] PM: Syncing filesystems ... done.
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  410.237445] Freezing user space processes ... (elapsed 0.01 seconds) done.
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  410.252273] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  410.268063] PM: Preallocating image memory... done (allocated 65680 pages)
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.528201] PM: Allocated 262720 kbytes in 1.26 seconds (208.50 MB/s)
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.528205] Suspending console(s) (use no_console_suspend to debug)
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.529570] eth1: Going into suspend...
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.529648] b44 0000:02:00.0: PCI INT A disabled
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.529655] ACPI handle has no context!
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.549599] ipw2200 0000:02:03.0: PCI INT A disabled
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.549605] ACPI handle has no context!
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.549821] Intel ICH 0000:00:1f.5: PCI INT B disabled
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.732035] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.732281] PM: freeze of drv:sd dev:0:0:0:0 complete after 202.829 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.732296] PM: freeze of drv:scsi dev:target0:0:0 complete after 202.820 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.732308] PM: freeze of drv:scsi dev:host0 complete after 202.758 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.732433] ata_piix 0000:00:1f.1: PCI INT A disabled
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  411.732439] PM: freeze of drv:ata_piix dev:0000:00:1f.1 complete after 182.588 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.237383] PM: freeze of drv:radeon dev:0000:01:00.0 complete after 707.693 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.237399] PM: freeze of drv:pci dev:0000:00:01.0 complete after 687.480 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.237413] PM: freeze of drv: dev:pci0000:00 complete after 687.469 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.237421] PM: freeze of devices complete after 709.010 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.238217] PM: late freeze of devices complete after 0.790 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.240143] ACPI: Preparing to enter system sleep state S4
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.240528] PM: Saving platform NVS memory
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.240541] PM: Saving platform NVS memory
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.240544] Disabling non-boot CPUs ...
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.240585] PM: Creating hibernation image:
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.244033] PM: Need to copy 65650 pages
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.244033] PM: Normal pages needed: 65650 + 1024, available pages: 65217
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.244033] PM: Not enough free memory
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.244033] PM: Error -12 creating hibernation image
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.244033] ACPI: Waking up from system sleep state S4
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.247672] yenta_cardbus 0000:02:01.0: O2: enabling read prefetch/write burst
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.248777] PM: early recover of devices complete after 1.239 msecs
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.276229] pm_op(): pci_pm_thaw+0x0/0x80 returns -16
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.276234] PM: Device 0000:00:00.0 failed to recover async: error -16
Jan  3 16:47:17 lido-Inspiron-600m kernel: [  412.276268] pci 0000:00:1e.0: setting latency timer to 64
```

Is the problem that my swap partition isn't big enough?

---

### Post by cipherboy_loc on 2011-01-03
Most likely. What is the output of:

```

swapon -a ; free -tm

```

The first command mounts all swap images in FSTAB, the second checks the amount of memory that is free.

Cipherboy

> **Lido said:**
> Thanks. How much ram do you have? I'm getting the error messages:

PM: Not enough memory
PM: Error -12 creating hibernation image

from syslog:

[removed to reduce the length of the post]
Is the problem that my swap partition isn't big enough?

---

### Post by Lido on 2011-01-04
> **cipherboy_loc said:**
> Most likely. What is the output of:

```

swapon -a ; free -tm

```


Thanks:

```
free -tm
             total       used       free     shared    buffers     cached
Mem:           496        444         52          0         39        215
-/+ buffers/cache:        189        306
Swap:         1495          0       1495
Total:        1992        444       1548

```

---

### Post by cipherboy_loc on 2011-01-04
It looks like you should have enough Swap space for it to work. Try starting up your computer, don't open anything, and then put it in hibernate right away (as soon as you log in).


Cipherboy

---

### Post by Lido on 2011-01-05
> **cipherboy_loc said:**
> It looks like you should have enough Swap space for it to work. Try starting up your computer, don't open anything, and then put it in hibernate right away (as soon as you log in). Cipherboy

That seems to work ok, though there's an error that shows up on the screen something about failed to thaw error -16 and one other message but also with the -16 error. It shows up in the screen, but there's something different in the syslog. The pm-suspend log seems ok (lots of thaw/hibernate success entries). Unfortunately, it only blanks the screen when I try to hibernate with anything running (ie text editor or browser etc).

Here are the hopefully relevant lines from syslog after seemingly successful hibernate with no applications open:

```
Jan  5 16:09:11 lido-Inspiron-600m wpa_supplicant[922]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  5 16:09:11 lido-Inspiron-600m avahi-daemon[799]: Withdrawing address record for 192.168.1.138 on eth1.
Jan  5 16:09:11 lido-Inspiron-600m avahi-daemon[799]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.138.
Jan  5 16:09:11 lido-Inspiron-600m avahi-daemon[799]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  5 16:09:11 lido-Inspiron-600m NetworkManager[782]: <info> (eth1): cleaning up...
Jan  5 16:09:11 lido-Inspiron-600m NetworkManager[782]: <info> (eth1): taking down device.
Jan  5 16:09:11 lido-Inspiron-600m avahi-daemon[799]: Interface eth1.IPv6 no longer relevant for mDNS.
Jan  5 16:09:11 lido-Inspiron-600m avahi-daemon[799]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::212:f0ff:fe36:a6e0.
Jan  5 16:09:11 lido-Inspiron-600m avahi-daemon[799]: Withdrawing address record for fe80::212:f0ff:fe36:a6e0 on eth1.
Jan  5 16:09:12 lido-Inspiron-600m kernel: [ 1564.358053] PM: Marking nosave pages: 0000000000002000 - 0000000000010000
Jan  5 16:09:12 lido-Inspiron-600m kernel: [ 1564.358059] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Jan  5 16:09:12 lido-Inspiron-600m kernel: [ 1564.358064] PM: Basic memory bitmaps created
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.358066] PM: Syncing filesystems ... done.
Jan  5 16:10:43 lido-Inspiron-600m acpid: client 891[0:0] has disconnected
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.761616] Freezing user space processes ... (elapsed 0.03 seconds) done.
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.792051] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.808068] PM: Preallocating image memory... done (allocated 65680 pages)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.903313] PM: Allocated 262720 kbytes in 0.09 seconds (2919.11 MB/s)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.903317] Suspending console(s) (use no_console_suspend to debug)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.904573] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.904764] eth1: Going into suspend...
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.924937] Intel ICH 0000:00:1f.5: PCI INT B disabled
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.925084] ata_piix 0000:00:1f.1: PCI INT A disabled
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.925135] ipw2200 0000:02:03.0: PCI INT A disabled
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.925141] ACPI handle has no context!
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.925149] b44 0000:02:00.0: PCI INT A disabled
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.925155] ACPI handle has no context!
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.970401] PM: freeze of devices complete after 66.872 msecs
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.971204] PM: late freeze of devices complete after 0.797 msecs
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.973140] ACPI: Preparing to enter system sleep state S4
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.973470] PM: Saving platform NVS memory
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.973483] PM: Saving platform NVS memory
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.973486] Disabling non-boot CPUs ...
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.973529] PM: Creating hibernation image:
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.976032] PM: Need to copy 63964 pages
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.976032] PM: Normal pages needed: 63964 + 1024, available pages: 66903
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.976032] PM: Restoring platform NVS memory
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.976032] ACPI: Waking up from system sleep state S4
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980717] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x20020200, writing 0x200a0200)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980777] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800003, writing 0x2800007)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980808] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980897] b44 0000:02:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980917] yenta_cardbus 0000:02:01.0: restoring config space at offset 0xf (was 0x14001ff, writing 0x58001ff)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980936] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x3 (was 0x822000, writing 0x82a800)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980943] yenta_cardbus 0000:02:01.0: restoring config space at offset 0x1 (was 0x4100007, writing 0x4100087)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980964] yenta_cardbus 0000:02:01.0: O2: enabling read prefetch/write burst
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980979] yenta_cardbus 0000:02:01.1: restoring config space at offset 0xf (was 0x14001ff, writing 0x58001ff)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.980998] yenta_cardbus 0000:02:01.1: restoring config space at offset 0x3 (was 0x822000, writing 0x82a800)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.981005] yenta_cardbus 0000:02:01.1: restoring config space at offset 0x1 (was 0x4100007, writing 0x4100087)
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1564.982120] PM: early restore of devices complete after 1.661 msecs
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1565.011382] pm_op(): pci_pm_restore+0x0/0xa0 returns -16
Jan  5 16:10:43 lido-Inspiron-600m kernel: [ 1565.011387] PM: Device 0000:00:00.0 failed to restore async: error -16
```

---

### Post by Lido on 2011-01-10
Ok, well it really doesn't seem like the problem is swap space, because I just did a clean install with 2.5GB of swap which should be plenty for this machine (I think it's got about 768MB of ram). Still getting this error in syslog when I try to hibernate with any open applications:
```
Jan 10 15:38:06 Dell-Inspiron-600m kernel: [  627.207462] PM: Creating hibernation image:
Jan 10 15:38:06 Dell-Inspiron-600m kernel: [  627.208267] PM: Need to copy 65660 pages
Jan 10 15:38:06 Dell-Inspiron-600m kernel: [  627.208267] PM: Normal pages needed: 65660 + 1024, available pages: 65207
Jan 10 15:38:06 Dell-Inspiron-600m kernel: [  627.208267] PM: Not enough free memory
```

---

### Post by forumache on 2011-01-17
I had hibernate working perfectly on Ubuntu 10.04 on a HP Mini 311.
On the same laptop I have now 10.10 and hibernate does not work (maybe, once in a while it might work, but I don't trust it).
So, we have an regression...

This was an old bug. When I'll reach home I'll try the following fix:

echo 0 > /sys/power/image_size

If you try and it works, please confirm.

Good luck.

---

