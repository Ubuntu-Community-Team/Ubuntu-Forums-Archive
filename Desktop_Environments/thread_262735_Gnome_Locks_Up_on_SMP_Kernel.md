---
title: "Gnome Locks Up on SMP Kernel"
date: 2006-09-22
forum: Desktop Environments
---

### Post by MattM on 2006-09-22
OK, I initially installed the 386 kernel with no problems. But this is a dual CPU system, so, I used synaptic to get the linux-686-smp kernel (a total of 5 packages). It installed without any issues.

From the very first time I booted the new kernal, Gnome locks up. It gets as far as the login screens, accepts username and password, then, when it should be displaying the window manager & Gnome startup progress, it just freezes.  Display, mouse, keyboard all locked up, have to hard power cycle to get out.  This is consistant on every boot attempt.

Went back to the 386 kernal via grub - it booted and ran GDM with no problems. Then tried 686 recovery mode.  Boots OK and I confirmed that it sees both CPUs. Then I tried starting GDM from the shell with a "/etc/init.d/gdm start" and got the same behavior: username and password screens, then freeze.

System is a PII x 2, Intel 440BX chipset, ATI Radeon 7000.  Ubuntu install is new - no mods to kernel, not a lot of added packages.

Are there updated GDM files needed for SMP that I don't know about? How about known Radeon issues? Found one tip on changing the driver name in xorg.conf from "ati" to "radeon", but that had no effect.

Any clues appreciated!

---

### Post by ghettobilly on 2006-09-22
you might want to check your memory but also a problem ive had with dual p3-800 of mine is to turn agp fastwrites off in bios fixed some random lockups on X start. though it might not make a differance as my chipset is via and my video card is gforce4

---

### Post by MattM on 2006-09-22
Thanks for the tip, I checked my BIOS, but I don't seem to have a setting for AGP fastwrites.

I continued playing around this evening and I think I found the problem!  However the solution remains elusive...

By using the "Options" menu on the login screen, I tried "GNOME Failsafe".  It still locks up, but shortly after displaying this error message:

> Power Manager

This program cannot start until you start the dbus session service.

This is usually started automatically in X or gnome startup when you start a new session.

So I went into the BIOS and started playing with the power management settings.  I figure the 386 kernel doesn't do much with power management, but the 686 kernel does.  By setting "ACPI Aware O/S" to true in BIOS, the system successfully boots, GDM starts, and the System Monitor shows both CPUs.  :D 

However, it consistantly locks up again within 5 minutes.  :sad:

I guess I'll just keep messing with the power management settings until I find something that works.

---

### Post by ghettobilly on 2006-09-22
try adding no-hlt to grub
i have a very old dual p166 that wont run whithout no-hlt
only drawback is cpu`s are at full power all the time

---

### Post by MattM on 2006-09-22
Tried no-hlt, no difference.  Still locks up after a few minutes.  I'm in "random guess" mode now - Maybe I'll hit on something that works.  

I wonder, is there a 686 non-SMP kernel?  I guess I can just set MAXCPUS=1 in the boot command.  That way, maybe I can isolate whether it is the 686 part or the SMP part that's dying. I'm still suspicious of power management - Found quite a few threads with complaints on that.

---

### Post by MattM on 2006-09-25
OK, learned some more...

The 2.6.15-27-686 Kernel boots OK with the MAXCPUS=1 directive, however, it crashes within 4 hours or so.  The 2.6.15-23-686 Kernel (also with the MAXCPUS=1 directive) is the same.

Found this page: [http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/ch03s06.html](http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/ch03s06.html)

It had some additional BIOS recommendations that were different than the setup I had.  Tuned the BIOS and rebooted with 2.6.15-27-686 (still with the MAXCPUS=1 directive).  So far, it's been running for a day.  I'll try removing the MAXCPUS option next to allow it to go SMP.  However, it initially looks like the BIOS changes may have improved things, primarilly changes to power management and shadow RAM settings.

---

### Post by Matt Yun on 2006-10-04
I've been having hanging lockups with the 2.6.15 SMP kernel too, on a dual PIII-800 machine.  Usually I can log in, but the machine hangs after about 30 min of use, after operations like scp and updatedb.

I've googled this subject for hours and have tried tinkering with different video cards, APM and ACPI, and console-only login, all to no avail.  

I've used different distros with SMP kernels, with different results:  Arch Linux also hangs, but Knoppix 3.9 doesn't.  I may try further distros if I have the time.

I get the same problem with the non-SMP 686 kernel, but not with the 386 kernel.  I tried compiling a 2.6.15-386-smp kernel (the only options I changed from the default Ubuntu config was enabling SMP for 2 cpus), but that also led to hanging.

Fortunately, I still have the Ubuntu 2.6.10-smp kernel left over from Hoary, and it works fine with no hanging, so that is my current default.

I'm wondering if the problem is with the reiserfs filesystem driver.  My / mount is currently reiserfs; I'm going to try experimenting with different filesystems to see if that makes a difference.

---

### Post by Matt Yun on 2006-11-03
I managed to successfully fix this problem.  I compiled a vanilla Linux 2.6.18 kernel from kernel.org with SMP-386 support, initially with no patches and with no changes to the default .config other than selecting 386 (SMP is default).

Everything appeared to work fine, except that I had problems mounting partitions in my secondary hard drives.  I came across this thread: 
[Solved: "Mounting Local Filesystems" fails after compiling new kernel]("http://ubuntuforums.org/showthread.php?t=103900"), so I patched the kernel with the evms (Enterprise Volume Management System) patch and recompiled.

I also elected, in menuconfig, to compile support for ext2/3, reiserfs, jfs, xfs, FUSE and ATA/IDE rather than have loadable modules for these.

Now my custom 2.6.18-386-smp-evms kernel is working fine in my dual-PIII box, with a current uptime of 5 days.  I've put it through some fairly heavy load, including simultaneous bittorrenting, transcode, rsyncing etc.

So it seems that the SMP hanging problems may be related to the performance patches that Ubuntu uses. When I have time (hah!), I'll try compiling kernels one patch at a time and see which patch causes the lockups.  I'll even try to figure out how to file a kernel bug report.

Here is the recipe I used (as root throughout, I don't get the fakeroot method)

```
# apt-get install ncurses-dev kernel-package bin86 linux-source build-essential

# apt-get install kernel-patch-evms

# cd /usr/src && wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.tar.bz2) 

# tar xvjf linux-2.6.18.tar.bz2

# cd /usr/src/kernel-patches/diffs/evms-bd-claim && gzip -d 2.6-bd-claim.patch.gz

# cd /usr/src/linux-2.6.18

# cat /usr/src/kernel-patches/diffs/evms-bd-claim/2.6-bd-claim.patch | patch -p1

# make menuconfig

# make-kpkg clean
# make-kpkg --initrd --append-to-version=-386-smp-evms kernel_image kernel_headers

# cd /usr/src

# dpkg -i kernel-image-2.6.18-386-smp-evms*.deb kernel-headers-2.6.18-386-smp-evms*.deb

```
And adjust GRUB to taste.

---

