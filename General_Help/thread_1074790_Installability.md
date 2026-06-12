---
title: "Installability?"
date: 2009-02-19
forum: General Help
---

### Post by Linkhed on 2009-02-19
I recently installed Wubi Ubuntu 8.10 on a machine with Vista. I instated a boot line by BCEdit with Ubuntu as default and a Timeout of 30. I restarted and it booted into Ubuntu. All well! Until I was unable to get Nvidia proprietary drivers installed and then I noticed Vista boot loader was booting straight into Ubuntu skipping choice of both options available. I tried inserting Vista disc and running startup recovery which returned no errors. I'm stuck with bad resolution and no way to get into Windows for unsupported applications.

[ 4340.084105] kvm: disabled by bios
[ 5745.705045] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[ 5745.705048] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0001:00.0)
[ 5745.705054] NVRM: The system BIOS may have misconfigured your graphics card.
[ 5745.706557] nvidia: probe of 0000:01:00.0 failed with error -1
[ 5745.707019] NVRM: The NVIDIA probe routine failed for 1 device(s).
[ 5745.707231] NVRM: None of the NVIDIA graphics adapters were initialized!

*@ubuntu:~$ sudo modprobe nvidia
FATAL: Error inserting nvidia (/lib/modules/2.6.27-11-generic/updates/dkms/nvidia.ko): No such device

---

