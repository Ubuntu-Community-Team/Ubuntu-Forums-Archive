---
title: "Kubuntu sticky window leftover"
date: 2013-12-01
forum: Desktop Environments
---

### Post by CWMAR30 on 2013-12-01
Hello I am running Kubuntu 12.04 --- For the longest time NOTHING 12.04 would install on here tried it again and 12.04.3 is working fine... I even have confirmation that the usb iso was good if it needs to be presented

When having apps open sometimes their window sticks after you close.. Like for instance closing the bookmarks tab in Firefox the window will turn the color of the window that greyish color for about 10 sec then finally dissapears off the screen like its trying to close... Meaning you click off the menu and you still see the outline for a few secs...

When changing the password for the setup of the guest account because it forced me to change it everything like froze.... and I had to do alt prnt scrn k when it told me it was too short all the wording dissapeared from the box and all I could see was a grey box. 

Just installed Kubuntu the other night. here is my system info... Can you tell me why this is happening? I am running not in FAILSAFE but the one above it FAILSAFE  KDE PLASMA and it seem responsive so far. 

this is a cous. built pc

MEMORY IN USE AS I WRITE THIS:  656 megs out of 2 gigs

Thank you,
Christopher



chris@COMPAQ:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
stepping        : 10
microcode       : 0xa07
cpu MHz         : 1600.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips        : 5866.44
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
stepping        : 10
microcode       : 0xa07
cpu MHz         : 1600.000
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips        : 5866.56
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

chris@COMPAQ:~$

---

### Post by TomB30 on 2013-12-01
KDE should win an award for being by far the best desktop that doesn't work.

I love Qt.  I like KDE and KDevelop really well, too.  I'd love to be using KDE right now but I've been using Gnome for the last year and I absolutely hate it.  I thought I'd learn to like it but that has proven to be a task beyond my ability.

It used to be akonadi that ruined the KDE experience.  I still miss KMail, akregator, etc.  Those haven't worked for years, for me.

The most recent treat out of the KDE camp seems to be some sort of malware integrated into the desktop.  A fresh Kubuntu install will leave my system sluggish.  "iftop" reveals thousands of sockets connecting to half the planet, directly after booting a fresh install.  I've tried Kubuntu (a few version), Mint 14/15, and ubuntu with kde-full.  All have the same behavior.

I'd switch to Windows but I have an i7 laptop (HP) with 8GB of RAM, Windows 7, and by the time you get AV and Outlook running, full screen YouTube stutters.  Sure, I could try a bunch of video drivers but it ought to play YouTube full screen, without stuttering, out of the box.  Seriously.

It's been a year since I've compiled KDE from source.  That experiment was semi-successful.  It ran OK for a few months and was taken out by Ubuntu package management problems.  According to this forum, I'm the only one who has had CUPS problems.

Gnome does everything I need to do, and Ubuntu 13.10 has been stable for a couple of months here, it just goes out of it's way to inconvenience me at every turn.

I know this post is hugely negative and entirely unhelpful but I think you'll have a hard time finding a stable KDE environment.  It can be made to function but it's a lot of work.  If you find a stable KDE platform (more than 3 days between running into issues), please report back.  I would dearly love to know how you did it.

---

