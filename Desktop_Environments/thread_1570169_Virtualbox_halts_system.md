---
title: "Virtualbox halts system"
date: 2010-09-07
forum: Desktop Environments
---

### Post by larynx on 2010-09-07
I'm running VirtualBox 3.2.8 r64453 on Ubuntu 10.04 32-bit (kernel 2.6.32-24-generic-pae), I created a new virtual machine to install Windows XP on (I haven't installed anything on it yet) and when I press the Start button my computer halts, the keyboard and mouse don't respond and the only way to restart it is by pressing the restart button on the box.

The host specs are:
Intel E8600 3.33Ghz
4GB DDR2
600GB (2 x WDC WD3200AAJS) RAID-0 (FakeRAID)
nVidia Quadro FX560

I tried checking the VirtualBox log but nothing is in it. I tried disabling the sound, network, 2D and 3D acceleration on the virtual machine but it still halts. What could be the issue?

---

### Post by QIII on 2010-09-07
How many cores did you assign to the virtual machine?

Where did you put the .vdi?

---

### Post by larynx on 2010-09-07
I assigned one core to the virtual machine.
The vdi file is located in /home/username/.VirtualBox/HardDisks

---

### Post by QIII on 2010-09-07
I tried a little googling.  Didn't find much except that it looks like you posted this on a virtualbox forum (good move!).

I don't think a RAID arrangement should pose a problem.  But I typically try to put my .vdis on a separate physical drive.  That eliminates competition for read/write operations with the host OS's drive.

If you don't have anything on your .vdi, it would be at least worth a shot deleting the machine and the .vdi and starting over.  Nothing lost at this point.

Be sure to look at VirtualBox.xml (should be in /home/foo/.virtualbox , depending on how you installed.)  Clean up any entries in MachineRegistry and MediaRegistry for that machine and .vdi to be sure you get a clean start.

I didn't ask how much memory you assigned to the virtual machine.

OSE or PEUL?

---

### Post by larynx on 2010-09-09
I tried both suggestions but it still won't work.

I assigned 1GB out of 4GB to the virtual machine and i'm running VirtualBox PUEL.

---

### Post by QIII on 2010-09-09
Is your XP .vdi associated with a SATA controller or an IDE controller in your VirtualBox set up?

---

### Post by larynx on 2010-09-09
After a lot of tinkering with the settings I found the culprit, as soon I checked off the "Enable VT-x/AMD-V" option in the Acceleration Tab inside the System settings the virtual machine booted with a problem.

Even though my CPU supports the VT-x extension it doesn't work. I still haven't managed to find out a workaround for this but at least it works.

---

