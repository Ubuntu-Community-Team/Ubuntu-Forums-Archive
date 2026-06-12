---
title: "Reboot during fetchmail install/update"
date: 2005-07-28
forum: Desktop Environments
---

### Post by Mr.Mechano on 2005-07-28
Holy shit!

Never saw a problem like this on any Debian and derived distribution.

I've two PCs, a laptop Dell Inspiron 6000 (Celeron M 360) and a small server with cheap Asrock K7S41GX with Sempron 2800+ CPU 512M DDR 400Mhz.

I've Kubuntu on both machines.

I did and apt-get update and apt-get ungrade and saw there were some updates for KDE libs, firefox 1.0.6 and fetchmail 6.2.5.

On the laptop everything was smooth.

But on the Sempron machine when dpkg tries to configure fetchmail the computer hangs and reboot is done.  :-| 

I've tested memory, CPU temperature, nothing is bad. 
If try and apt-get install of every package than fetchmail I'm able to install every update, but fetchmail reboot the computer. 

I've downloaded a Mandriva version of fetchmail and converted into .deb package using alien, dpkg -i installed it.

The package into the ubuntu repository seems malformed or broken, but it's strange because on the laptop it was installed smootly.

__
Mr. Mechano

---

### Post by Mr.Mechano on 2005-08-05
Found the solution.

I've a root partition with Reiser File System.
During last instability problem and system hangs and reboot the file system got corrupted.
Some files into /usr/share/doc/fetchmail were corrupted.

So I've been obliged to boot with a livecd distribution and launch this commands:

fsck.reiserfs /dev/hdax (x the root partition)
fsck.reiserfs --fix-fixable /dev/hdax
fsck.reiserfs --rebuild-db /dev/hdax

After all I've been able to upgrade my distribution!  \\:D/ 

__
Mr. Mechano

---

