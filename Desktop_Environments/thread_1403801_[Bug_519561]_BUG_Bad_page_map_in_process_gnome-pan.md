---
title: "[Bug 519561] BUG: Bad page map in process gnome-panel  pte:00000001 pmd:1c4a6067"
date: 2010-02-10
forum: Desktop Environments
---

### Post by nkbatsi on 2010-02-10
**[Bug 519561]**




BUG: Bad page map in process gnome-panel  pte:00000001 pmd:1c4a6067
[https://bugs.launchpad.net/bugs/519561](https://bugs.launchpad.net/bugs/519561)
You received this bug notification because you are a direct subscriber
of the bug.

Status in “linux” package in Ubuntu: New

hello,
i'm new in ubuntu, the problem is that my system goes unstable from time to time refusing to
start applications like firefox. amule. even synaptic manager or update manager.
in some cases the system crashed not even being able to change terminal.

i' m planning to get a little tiring now. i' m going to write my story about my computer!
i have studied computer technology (not programming) and tried to use linux  10 years ago (mandrake i believe it was)
  but switched back to windows cause it was easiest for my studies (internet at that times was hell in my country so linux
was really hard to use) and support much poorer.

now i'm back to linux again using ubuntu 9.10 karmic distro, sick and tired of blue screens and with a machine of poor performance.
i believed that this would be no problem for ubuntu since i did my studying and found out that my pc was able to handle ubuntu distro, didn't choose any other distro like kubuntu or xubuntu even if they were more suitable to my machine because i knew there would be minor differences between distros and was sure that help and support for ubuntu full version would be far more easier to get.
  
i had to borrow my little sisters laptop to download ubuntu and xubuntu then really very slowly burned them to iso cds, i also borrowed a 9.04 iso cd from a friend.

here starts my nightmare!
i tried every possible way and every cd i had in my hands (more than 10) many many times. as i mentioned the 9.04 version was already tested to work on other computers.
  the outcome was a disaster, live cds operating but not installing. installation cds working but computer not booting.

my first success was an alternate cd of xubuntu, kernel installed but no gui!
did a little googling and managed to install a gui to find out a couple of hours later that the system was far too unstable to operate.
  it was hell.

9.04 worked once, then tried to update and my system went corrupt. the boot loader could find no os's on disks!
from then on i started trying to install in every possible way with every possible means and much help from the internet.

tried direct installing from cd's, or booting up with a live cd and then installing. everything was unstable, some times the same cd worked, some times not. found out that ubuntu installation was responding better when done on fresh made partitions (i needed partitions, some data is valuable). 
  
so the drill went on like this for many times (maybe more than 50):
-creating new partions (just resizing each time)
-full formating each time (not quick)
-intalling ubuntu

each and every time something went wrong throughout the installation progress (i repeat : many different iso cds were used).
forgot to mention that through this long process i was also changing features in my bios (loading fail-safe mode or decreasing memory speed hoping to make my system stable enough for ubuntu to install on (the system is not boosted in any way)).
  
finally i did this:
- plugged two hdds in the same ide one 15 GB and one 500 GB
- set 15 GB as master
- installed windows xp pro on it (yes that sucks but i needed to be sure that i would have at least one lousy os).
  - then set 500 GB as master and 15 GB as slave
- installed ubuntu 9.10 karmic on partition of 500 GB 

the last installation was partly successful (after many many tries) giving me a couple of notifications!
 now i've got a dual boot pc with the option to toggle jumpers in my disks and make it windows boot only since its MBR is intact.
clever solution he he he ;)

YES i' m a very stubborn man! now ubuntu works (kind of slow and unstable though).
the general idea was to experiment!

now here' s what i' ve done since my system kind of started to function tolerably:
  
installed amule which needed ports, after a little googling (ubuntu users tips are very helpful -- special thanks to all of them!) i decided to install firestarter which at that time, with all that rules to be added, did not help at all (still trying to figure out what the address from my pc to my gateway and what my address from my gateway to the internet is and which one of them firestarter needed to be added in its rules).
  
next discovery : firestarter is not needed in order for ports to be open, they just open up when they are listened to !!! what a surprise! everything is so easy and so complicated...

uninstalled firestarter and then i get error messages about fatal errors about the kernel.
  amule would not start.
firefox would not start.
synaptic package manager would not start.
update manager would not start.

after many boot ups and unistalling amule (which came out to be no problem) the system seems to be operating good enough.
  i even reinstalled amule which is now operating in a mysterious way:
the first time the system boots amule starts ok when clicked on but if i close it and try to start it again it is a gamble whether it will start or not!
sometimes the screen just flashes like it is going to open up a new window, i wait for emule to start but nothing happens, not even a tab opening in the lower taskbar. other times it just starts a few seconds later.

  same goes for firefox:
sometimes starts fine after booting up sometimes not (screen flashing as if to open a new window, but in this case a tab opens up at the lowest taskbar saying "starting firefox" then just closes) 
also sometimes firefox closes down unexpectedly during session, even when i do nothing heavy, just like when writing a message in gmail, for instance, with no other firefox tabs open (this also happens in windows xp).
  
something similar goes on with synaptic and update manager. the former has three options:
1- starts fine - works fine, installs - uninstalls fine
2- won't start (screen flashes etc.)
3- system crashes when trying to start synaptic (no Ctrl+Alt+F1 or F2 etc operating)
  the latter just one:
1- not starting!

similar for rythmbox, movieplayer etc.

when i check system monitor the most of my CPU usage is taken by system monitor itself than all other applications together.(CPU flashes to 100% only when clicking on an application to start it but i believe this is common)
  given the past problems i' m afraid to update my kernel and system.

anybody out there please HELP!!!

thanks in advance for reading my novel... 

my system configuration follows.

attachments too (might be needed)



ProblemType: KernelOops
Annotation: Your system might become unstable now and might need to be restarted.
Architecture: i386
AudioDevicesInUse:
 USER        PID ACCESS COMMAND
 /dev/snd/controlC0:  nkbatsi    1252 F.... pulseaudio
 /dev/snd/timer:      nkbatsi    1252 f.... pulseaudio
CRDA: Error: [Errno 2] No such file or directory
[Card0.Amixer.info]("http://card0.amixer.info/"):
 Card hw:0 'Live'/'SB Live! 5.1 (rev.7, serial:0x80641102) at 0xe400, irq 5'
   Mixer name   : 'SigmaTel STAC9708,11'
   Components   : 'AC97a:83847608'
   Controls      : 224
   Simple ctrls  : 45
Date: Wed Feb 10 00:21:33 2010
DistroRelease: Ubuntu 9.10
Failure: oops
HibernationDevice: RESUME=UUID=2acfd000-5c3d-4d52-8f3f-fb702a1659fb
InstallationMedia: Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
Lsusb:
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
MachineType: VIA Technologies, Inc. VT8363
Package: linux-image-2.6.31-14-generic 2.6.31-14.48
ProcCmdLine: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=ff049705-bfe1-4642-a2f4-cc9b30c99400 ro quiet splash
ProcVersionSignature: Ubuntu 2.6.31-14.48-generic
RelatedPackageVersions:
 linux-backports-modules-2.6.31-14-generic N/A
 linux-firmware 1.24
RfKill:
 0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
SourcePackage: linux
Tags: kernel-oops
Title: BUG: Bad page map in process gnome-panel  pte:00000001 pmd:1c4a6067
Uname: Linux 2.6.31-14-generic i686
dmi.bios.date: 07/28/2000
dmi.bios.vendor: Award Software International, Inc.
dmi.bios.version: 6.00 PG
[dmi.board.name]("http://dmi.board.name/"): 8363-686A
dmi.board.vendor: Legend.QDI,Inc
dmi.board.version: KINETIZ 7T
dmi.chassis.type: 3
dmi.modalias: dmi:bvnAwardSoftwareInternational,Inc.:bvr6.00PG:bd07/28/2000:svnVIATechnologies,Inc.:pnVT8363:pvr:rvnLegend.QDI,Inc:rn8363-686A:rvrKINETIZ7T:cvn:ct3:cvr:
[dmi.product.name]("http://dmi.product.name/"): VT8363
dmi.sys.vendor: VIA Technologies, Inc.

** Affects: linux (Ubuntu)
     Importance: Undecided
         Status: New


** Tags: apport-kerneloops i386 kernel-oops



 

** Attachment added: "AlsaDevices.txt"
   [http://launchpadlibrarian.net/38947858/AlsaDevices.txt](http://launchpadlibrarian.net/38947858/AlsaDevices.txt)

** Attachment added: "AplayDevices.txt"
   [http://launchpadlibrarian.net/38947861/AplayDevices.txt](http://launchpadlibrarian.net/38947861/AplayDevices.txt)

** Attachment added: "ArecordDevices.txt"
   [http://launchpadlibrarian.net/38947863/ArecordDevices.txt](http://launchpadlibrarian.net/38947863/ArecordDevices.txt)

** Attachment added: "BootDmesg.txt"
   [http://launchpadlibrarian.net/38947865/BootDmesg.txt](http://launchpadlibrarian.net/38947865/BootDmesg.txt)

** Attachment added: "Card0.Amixer.values.txt"
   [http://launchpadlibrarian.net/38947866/Card0.Amixer.values.txt](http://launchpadlibrarian.net/38947866/Card0.Amixer.values.txt)

** Attachment added: "Card0.Codecs.codec97.0.ac97.0.0.txt"
   [http://launchpadlibrarian.net/38947868/Card0.Codecs.codec97.0.ac97.0.0.txt](http://launchpadlibrarian.net/38947868/Card0.Codecs.codec97.0.ac97.0.0.txt)

** Attachment added: "Card0.Codecs.codec97.0.ac97.0.0.regs.txt"
   [http://launchpadlibrarian.net/38947870/Card0.Codecs.codec97.0.ac97.0.0.regs.txt](http://launchpadlibrarian.net/38947870/Card0.Codecs.codec97.0.ac97.0.0.regs.txt)

** Attachment added: "CurrentDmesg.txt"
   [http://launchpadlibrarian.net/38947872/CurrentDmesg.txt](http://launchpadlibrarian.net/38947872/CurrentDmesg.txt)

** Attachment added: "Dependencies.txt"
   [http://launchpadlibrarian.net/38947874/Dependencies.txt](http://launchpadlibrarian.net/38947874/Dependencies.txt)

** Attachment added: "IwConfig.txt"
   [http://launchpadlibrarian.net/38947875/IwConfig.txt](http://launchpadlibrarian.net/38947875/IwConfig.txt)

** Attachment added: "Lspci.txt"
   [http://launchpadlibrarian.net/38947876/Lspci.txt](http://launchpadlibrarian.net/38947876/Lspci.txt)

** Attachment added: "OopsText.txt"
   [http://launchpadlibrarian.net/38947877/OopsText.txt](http://launchpadlibrarian.net/38947877/OopsText.txt)

** Attachment added: "PciMultimedia.txt"
   [http://launchpadlibrarian.net/38947879/PciMultimedia.txt](http://launchpadlibrarian.net/38947879/PciMultimedia.txt)

** Attachment added: "ProcCpuinfo.txt"
   [http://launchpadlibrarian.net/38947880/ProcCpuinfo.txt](http://launchpadlibrarian.net/38947880/ProcCpuinfo.txt)

** Attachment added: "ProcInterrupts.txt"
   [http://launchpadlibrarian.net/38947881/ProcInterrupts.txt](http://launchpadlibrarian.net/38947881/ProcInterrupts.txt)

** Attachment added: "ProcModules.txt"
   [http://launchpadlibrarian.net/38947883/ProcModules.txt](http://launchpadlibrarian.net/38947883/ProcModules.txt)

** Attachment added: "UdevDb.txt"
   [http://launchpadlibrarian.net/38947884/UdevDb.txt](http://launchpadlibrarian.net/38947884/UdevDb.txt)

** Attachment added: "UdevLog.txt"
   [http://launchpadlibrarian.net/38947885/UdevLog.txt](http://launchpadlibrarian.net/38947885/UdevLog.txt)

** Attachment added: "WifiSyslog.txt"
   [http://launchpadlibrarian.net/38947886/WifiSyslog.txt](http://launchpadlibrarian.net/38947886/WifiSyslog.txt)
- &#928;&#961;&#959;&#946;&#959;&#955;&#942; &#945;&#957;&#945;&#966;&#949;&#961;&#972;&#956;&#949;&#957;&#959;&#965; &#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965; -

---

