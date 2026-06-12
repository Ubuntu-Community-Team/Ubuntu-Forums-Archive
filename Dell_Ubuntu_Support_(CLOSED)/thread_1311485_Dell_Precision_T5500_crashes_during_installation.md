---
title: "Dell Precision T5500 crashes during installation"
date: 2009-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wiedehopf on 2009-11-02
Dear Ubuntu users,

I have recently purchased a Dell Precision T5500 (Intel Xeon CPU E5530 @ 2.40GHz, 24 GB DDR3 SDRAM, Nvidia Quadro FX 580).
The Computer was delivered with an installation of Red Hat Enterprise Linux Desktop 5.3 (kernel version 2.6.18-128, so a quite old kernel). When   trying to install Ubuntu on a second hard drive, the system froze during the install, i.e. did not react in any way to mouse or keyboard. This happened for the two newest Ubuntu versions, 9.04 and 9.10. With Linux Debian the same thing happens, although for Debian's stable release I managed (after several attempts) to complete the installation. However, after rebooting the system freezes within the next 20 minutes or so. Once the following error message was printed to the virtual console (not reproducible):

error message after 1560 seconds:

HARDWARE ERROR
CPU 0: Machine Check Exception:                4 Bank 5: 0000000000000000
TSC 0
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check


As this seemed to suggest a memory failure I ran the standard memory tests, which were all passed. I can run Debian Linux by copying the kernel and kernel modules from Red Hat, but this workaround does not appear to be very sustainable. Also, trying to stabilize the Debian system by fine-tuning the BIOS settings did not bring any success.

Does anyone have an idea why I have these issues with Debian and Ubuntu but not with Red Hat? I would appreciate any helpful suggestion. Also, if anybody has a similar system and managed to install Ubuntu, can he/she let me know please. Since, I haven't really found anything on the internet (and this Dell system should not be that exotic), I start to believe that my hardware is faulty and I will have to get back to Dell.

Kind Regards,

Andreas

---

### Post by curiouuser on 2010-04-20
Hi Man,


I have exactly the same problem. I bought T5500 from Dell (Duel Quad Intel 5500 2.9GHz- 72GB RAM).

It came with RedHat, I tried to install (under RAID 0) Ubuntu - 64bit desktop edition, it crashed in the initial state itself.

I could not do anything further. Anybody has same issues???

Peace

-Raj



> **Wiedehopf said:**
> Dear Ubuntu users,

I have recently purchased a Dell Precision T5500 (Intel Xeon CPU E5530 @ 2.40GHz, 24 GB DDR3 SDRAM, Nvidia Quadro FX 580).
The Computer was delivered with an installation of Red Hat Enterprise Linux Desktop 5.3 (kernel version 2.6.18-128, so a quite old kernel). When   trying to install Ubuntu on a second hard drive, the system froze during the install, i.e. did not react in any way to mouse or keyboard. This happened for the two newest Ubuntu versions, 9.04 and 9.10. With Linux Debian the same thing happens, although for Debian's stable release I managed (after several attempts) to complete the installation. However, after rebooting the system freezes within the next 20 minutes or so. Once the following error message was printed to the virtual console (not reproducible):

error message after 1560 seconds:

HARDWARE ERROR
CPU 0: Machine Check Exception:                4 Bank 5: 0000000000000000
TSC 0
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check


As this seemed to suggest a memory failure I ran the standard memory tests, which were all passed. I can run Debian Linux by copying the kernel and kernel modules from Red Hat, but this workaround does not appear to be very sustainable. Also, trying to stabilize the Debian system by fine-tuning the BIOS settings did not bring any success.

Does anyone have an idea why I have these issues with Debian and Ubuntu but not with Red Hat? I would appreciate any helpful suggestion. Also, if anybody has a similar system and managed to install Ubuntu, can he/she let me know please. Since, I haven't really found anything on the internet (and this Dell system should not be that exotic), I start to believe that my hardware is faulty and I will have to get back to Dell.

Kind Regards,

Andreas

---

### Post by curiouser on 2010-04-20
Yes.

As I said, I got the same problem with Dell T5500. Finally, I managed to see what's going on.

It is the graphics card issue. I tried to install Ubuntu Desktop with no graphics card support, it was a seamless installation. I shall update with more information on its stability in another 2 days.

peace

-Raj

---

### Post by esor_ekim on 2010-10-14
Similar problems with RHEL 5.5 (well, actually Scientific Linux 5.5) and a kickstart auto-install onto a T5500 (8 cores, 12GB memory and 3 of 1.5TB disks).

The installation would crash/freeze, repeatedly, just after the disk partitioning and formatting.

The Dell diagnostics (boot option from F12) found no problems, even running the extended memory tests.

The very odd thing was that a manual install of RHEL / SL 5.5 worked! repeatedly, then testing the machine with iozone to load it a bit was fine for several hours.

I had already removed the "display port" graphics card and replaced it with a simple nvidia, no fan, card.

I tried a lot of things and now have the auto installation working. I  wish I knew what exact thing I did actually caused success.

Things tried that did not produce success:
- smaller disk (160GB)
- defining the partitioning by hand at the start of the auto-install
- defining partitioning with a file so it was automated (fragment below)
- BIOS settings changes

The solution we found:

- set BIOS disks bit to RAID or AHCI
- disable RAID on all of the disks (ctrl I during post)
- wipe each disk, at least the start of them, using:
dd if=/dev/zero of=/dev/sda count=1024
this was done by booting to a manual Linux install then using the shell on one of the virtual consoles
automated kickstart install then worked



# Generated ks-fragment for new machine XXX
#
# Clear the partition table on sda
clearpart --all --drives=sda
#
# create 2 partitions, one for /boot, the other an lvm pv for the rest
part /boot --fstype ext3 --size=100 --ondisk=sda
part pv.6 --size=0 --grow --ondisk=sda
#
# make the pv into an lvm group
volgroup XXXXSys00 pv.6
#
# create  the lvm volumes on the group
logvol /    --fstype ext3 --name=root --vgname=XXXXSys00 --size=2048
logvol /usr --fstype ext3 --name=usr  --vgname=XXXSys00 --size=10240
logvol /var --fstype ext3 --name=var  --vgname=XXXXSys00 --size=2048
logvol swap --fstype swap --name=swap --vgname=XXXXSys00 --size=20480
logvol /tmp --fstype ext3 --name=tmp  --vgname=XXXXSys00 --size=10240
# the disk better be at *least* big enough for this
#logvol /local --fstype ext3 --name=scratch --vgname=XXXXSys00 --size=10240 --grow
#
# End of ks-fragment for XXXX

---

### Post by rengolin on 2011-09-23
> **curiouser said:**
> Yes.

As I said, I got the same problem with Dell T5500. Finally, I managed to see what's going on.

It is the graphics card issue. I tried to install Ubuntu Desktop with no graphics card support, it was a seamless installation. I shall update with more information on its stability in another 2 days.

peace

-Raj

I can confirm it's a graphic card issue. I just got the new kernel (via update) and it freezes when starting X. If I select recovery and go for failsafeX, everything works fine.

Sticking to the old kernel for now, until NVidia drivers are updated at the same time.

---

### Post by nothingspecial on 2011-09-23
Goodnight old thread.

---

