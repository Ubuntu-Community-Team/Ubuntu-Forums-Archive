---
title: "Troubleshooting custom kernel: disk drivers"
date: 2009-03-18
forum: General Help
---

### Post by cucio on 2009-03-18
Hi there!

If there's some kernel guru around, I could definitely use some help here.

Repository linux-rt kernels won't boot in my system, or will crash, or will fight tooth and nail with my wifi card, so I have decided to roll my own.

I am using linux-2.6.26.8.tar.bz2 plus patch-2.6.26.8-rt16.bz2, since it is recommended as a stable combination here.

[http://www.osadl.org/Latest-Stable.latest-stable-realtime-linux.0.html](http://www.osadl.org/Latest-Stable.latest-stable-realtime-linux.0.html)

So after make-kpkg'ing it and installing it I try to boot and the system gets stuck after the CDROM detection:

Uniform CD-ROM driver Revision: 3.20

After a couple of minutes some timer expires and I get a busybox shell where I can explore the initramfs.

There I have noticed that my IDE devices are detected as /dev/hd* instead of /dev/sd* when I use a regular kernel, so I wonder if this may cause the boot process to not find the root partition. My fstab is expressed in terms of UUIDs and the root partition is a lvm volume.

I wonder if I have forgotten some important option in the kernel config file or if I should somehow modify the default mkinitramfs configuration.

I attach my .config to the post.

When I use a generic kernel lsmod lists, among others, the following modules, which I believe are the only relevant ones to the problem at hand:

ext3, jbd, mbcache, sg, sr_mod, cdrom, sd_mod, ata_piix, ata_generic, pata_acpi, libata, scsi_mod, dm_mirror, dm_snapshot, dm_mod

Thanks in advance!

---

### Post by cucio on 2009-03-19
After some tests I have the impression that there is some mismatch between the userland lvm tools that get bundled in the initrd and the kernel 2.6.26 lvm modules.

At the busybox shell I perform 'lvm vgscan' and I get nothing. The dm modules are loaded.

I guess having a LV as your root partition is still problematic.

---

