---
title: "lxde and other problem"
date: 2022-07-05
forum: Desktop Environments
---

### Post by charonikh12 on 2022-07-05
I tried to install lxde, but some errors appear .

```
(Reading database... 288572 files and directories currently installed.)
Remove linux-image-5.15.0-25-generic (5.15.0-25.25) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-25-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 12: /etc/default/grub: scsi_mod.use_blk_mq=1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error while processing package linux-image-5.15.0-25-generic (--remove):
 installed linux-image-5.15.0-25-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors - stop
Errors occurred while processing the following packages:
 linux-image-5.15.0-25-generic
Processing stopped due to too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Then I went to google the answer, but for everything else I got only new errors. (by the way, these errors listed in this discussion are repeated on many other programs / drivers)

```
charonikh@kaplyaking:~$ sudo apt clean
charonikh@kaplyaking:~$ sudo apt autoclean
Reading Package Lists... Done
Building the dependency tree… Done
Reading Status Information… Done
charonikh@kaplyaking:~$ sudo apt autoremove
Reading Package Lists... Done
Building the dependency tree… Done
Reading Status Information… Done
You can run "apt --fix-broken install" to fix these errors.
The following packages have unmet dependencies:
E: Unmet dependencies. Try "apt --fix-broken install" without a package name (or a solution).
charonikh@kaplyaking:~$ sudo apt check
E: Invalid check operation
charonikh@kaplyaking:~$ sudo dpkg --configure -a
charonikh@kaplyaking:~$ sudo apt update


```


Then which actions go normally, and then again problems.


```
N: Skip getting customized "main/binary-i386-/Packages" file because "http://deb.xanmod.org releases InRelease" repository does not support "i386-" architecture
W: [https://dl.winehq.org/wine-builds/ubuntu/dists/focal/InRelease:](https://dl.winehq.org/wine-builds/ubuntu/dists/focal/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt -key(8) for details.
N: Skip getting customized file "main/binary-i386-/Packages" because repository "https://dl.winehq.org/wine-builds/ubuntu focal InRelease" does not support "i386-" architecture
W: Skipped getting the customized "universe/source/Sources" file because the "universe" component is missing from the "http://archive.canonical.com/ubuntu jammy InRelease" repository (perhaps the component is listed incorrectly in sources.list? )
W: Skipped getting the customized "multiverse/source/Sources" file because the "multiverse" component is missing from the "http://archive.canonical.com/ubuntu jammy InRelease" repository (perhaps the component is listed incorrectly in sources.list? )
```


And again problems...

---

### Post by charonikh12 on 2022-07-05
i really need answers.... i so tired. I was hacked into Windows 7, on my old laptop, and I decided to install Lubuntu on it for interest .. And here are the problems, honestly, guys, I&#8217;ll either burst into tears or throw it at the wall ..

---

### Post by guiverc on 2022-07-05
You've provided no release details; and in the second comment mention Lubuntu (LXQt), but have mentioned/highlighted LXDE in both which is a desktop Lubuntu no longer support.

The last eight releases of Lubuntu used LXQt (not LXDE) with LXDE being pure upstream Debian packages in those releases; Lubuntu no longer support LXDE (*and haven't since April 2021 when Lubuntu 18.04 LTS reached EOL*).

---

### Post by TheFu on 2022-07-05
Looks like there base system should be 22.04 "something" based on the 5.15.x kernel, but the PPAs say Focal, which is 20.04.  You cannot mix 20.04 and 22.04 repositories/PPAs.  That will never work.

LXDE isn't really supported on 22.04. Lubuntu is LXQt-base and has been for some time, as pointed out above.

Before posting, always do these things first:

```
sudo apt update
sudo apt full-upgrade
```

and if a reboot is needed from that, reboot and try your stuff again.  Usually, any errors from those 2 commands are due to PPA issues or screwed up repos.  When following online instructions, be 100% certain that the instructions:
a) come from a reputable website (until you learn which are reputable, stick with those with "ubuntu" in the DNS part of the URL)
b) are for the exact release version you are running.  ( the release is provided by this command  **lsb_release -d **)

As for gaming, I cannot help. Sorry.  Gaming on Linux has been oversold IMHO.  So has WINE. It just isn't that good 90% of the time, if it even works.  Years ago, I'd fight with WINE to get programs sorta working. They never fully worked.  Then the program would have a version update and that would break all the WINE configuration stuff.  After screwing around for 2-4 weeks trying to get the new program version working, I gave up and installed Windows into a virtual machine.  These were office-productivity apps, not games or graphics stuff, so the VM desktop performance was sufficient.  There was/is still one video editing program in Windows which never ran under a virtual machine. It wanted direct access to the GPU, which wasn't possible with a VM. For many years - over a decade - I I kept a Windows laptop just for that video editor.  Last fall, a Linux-based replacement finally became available and it has been updated 4 times since, getting better each time. It isn't as good as the Windows video editor I liked, but I can see the road map for the Linux one and see plans so I can move some editing keys to new keys which would make more sense.

BTW, when posting for help, some basic information is really helpful.  The easiest way to provide that is with a tool, **inxi -bxz**. the options strip sensitive data out.

For example, my 20.04 desktop:
```
$ inxi -bzx
System:    Kernel: 5.4.0-121-generic x86_64 bits: 64 compiler: gcc v: 9.4.0 Desktop: FVWM 2.6.7
           Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:   Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996) 
           v: pc-i440fx-xenial serial: <filter> 
           Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.10.2-1ubuntu1 
           date: 04/01/2014 
CPU:       2x Single Core (4-Die): AMD EPYC (with IBPB) type: MCM SMP arch: Zen 
           speed: 3409 MHz 
Graphics:  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
           bus ID: 00:02.0 
           Display: server: X.Org 1.20.8 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 
           direct render: Yes 
Network:   Device-1: Intel 82371AB/EB/MB PIIX4 ACPI vendor: Red Hat Qemu virtual machine 
           type: network bridge driver: piix4_smbus v: N/A port: c160 bus ID: 00:01.3 
           Device-2: Red Hat Virtio network driver: virtio-pci v: 1 port: c0e0 
           bus ID: 00:03.0 
Drives:    Local Storage: total: 40.00 GiB used: 23.90 GiB (59.7%) 
Info:      Processes: 182 Uptime: 3d 6h 58m Memory: 3.84 GiB used: 1.37 GiB (35.7%) 
           Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
           inxi: 3.0.38 
```
Simple, to the point. Covers most stuff.

---

