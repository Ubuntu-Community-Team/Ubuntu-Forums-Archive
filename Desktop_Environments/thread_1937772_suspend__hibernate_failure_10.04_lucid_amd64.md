---
title: "suspend / hibernate failure 10.04 lucid amd64"
date: 2012-03-08
forum: Desktop Environments
---

### Post by JasonAzat on 2012-03-08
Ubuntu 10.04 lucid on HP pavilion amd64 a6110n fails to suspend / hibernate.
1. Fails going into suspend or hibernate.  Hard disk spins down, cpu fan on, psu fan on.
    suspend: freeze on re-login screen, hard restart, starts over
    hibernate: freeze on blank screen (edit: or re-login screen),  hard restart, re-login screen
2. Happens every time.
3. Never has worked.
4. No flashing caps lock light seen.
5. Not a resume issue as far as I can tell
6. First install same issues, had all updates, HD radeon 5450 video  card, 2 gig swap.  Just did a fresh install, no updates, only internal  video, 5.5gig swap (tried with 2 and 4 gig ram), still happens.
7. Tested with upstream kernel, problem exists there too.  Also tried with some older kernels, problem seen there too, plus no GUI with older kernels.



Also put this on Launchpad, but thought I'd put it on here too to see if anyone here had any thoughts on working around this.


Thank you.

##################

More apport / log files and upstream kernel testing notes on launchpad.

Launchpad bug #946018
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/946018](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/946018)

 ProblemType: Bug
DistroRelease: Ubuntu 10.04
Package: linux-generic 2.6.32.38.44
Regression: No
Reproducible: Yes
ProcVersionSignature: Ubuntu 2.6.32-38.83-generic 2.6.32.52+drm33.21
Uname: Linux 2.6.32-38-generic x86_64
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.21.
Architecture: amd64
AudioDevicesInUse:
 USER        PID ACCESS COMMAND
 /dev/snd/controlC0:  azatubuntu   1363 F.... pulseaudio
CRDA: Error: [Errno 2] No such file or directory
Card0.Amixer.info:
 Card hw:0 'NVidia'/'HDA NVidia at 0xfe024000 irq 23'
   Mixer name    : 'Realtek ALC1200'
   Components    : 'HDA:10ec0888,103c2a58,00100101'
   Controls      : 37
   Simple ctrls  : 21
Date: Sat Mar  3 17:26:01 2012
HibernationDevice: RESUME=UUID=3821545f-0d65-4828-8f89-92b41f498edd
InstallationMedia: Ubuntu 10.04.4 LTS "Lucid Lynx" - Release amd64 (20120214.2)
IwConfig:
 lo        no wireless extensions.
  eth0      no wireless extensions.
MachineType: HP-Pavilion GG781AA-ABA a6110n
ProcCmdLine: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=ec0258c2-d39c-43a0-828d-ec2ebc3b8f6e ro quiet splash
ProcEnviron:
 LANG=en_US.UTF-8
 SHELL=/bin/bash
RelatedPackageVersions: linux-firmware 1.34.7
RfKill:
 SourcePackage: linux
dmi.bios.date: 05/04/2007
dmi.bios.vendor: Phoenix Technologies, LTD
dmi.bios.version: 5.08
dmi.board.name: NARRA2
dmi.board.vendor: ASUSTek Computer INC.
dmi.board.version: 2.00
dmi.chassis.type: 3
dmi.chassis.vendor: Hewlett-Packard
dmi.chassis.version: Chassis Version
dmi.modalias: dmi:bvnPhoenixTechnologies,LTD:bvr5.08:bd05/04/2007:svnHP-Pavilion:pnGG781AA-ABAa6110n:pvr:rvnASUSTekComputerINC.:rnNARRA2:rvr2.00:cvnHewlett-Packard:ct3:cvrChassisVersion:
dmi.product.name: GG781AA-ABA a6110n
dmi.sys.vendor: HP-Pavilion
 Ubuntu 10.04.4 LTS
 linux-generic:
  Installed: 2.6.32.38.44
  Candidate: 2.6.32.38.44
  Version table:
 *** 2.6.32.38.44 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
        100 /var/lib/dpkg/status
     2.6.32.21.22 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
 Ubuntu 2.6.32-38.83-generic 2.6.32.52+drm33.21

---

### Post by Sergius14 on 2012-03-08
You said that have tried with other Kernels, but to be sure, have you tried with more recents?.

Give a try to 3.2 if you didn't have done.

---

### Post by JasonAzat on 2012-03-08
tested upstream kernel
 tried with linux-image-3.2.0-18-generic and then



3.3.0-030300rc6-generic
from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc6-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.3-rc6-precise/")
 boots into gui.  Have my desktop etc.
 from terminal window: sudo pm-suspend
                screen freezes with last image, hard disk stops, cpu and psu fans stay on, unresponsive
         hard restart, opens clean desktop, lost settings
        sudo pm-hibernate
  screen flashes, freezes with following text:
[  62.773430] [drm] nouveau 0000:00:0d.0: =======0x0060081D=======
[  62.773430] [drm] nouveau 0000:00:0d.0: =======0x0060081D=======
, hard disk stops, cpu and psu fans stay on, unresponsive
  hard restart, opens all windows from last time.

---

