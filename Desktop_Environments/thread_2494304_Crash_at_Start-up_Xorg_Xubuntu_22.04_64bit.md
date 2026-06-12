---
title: "Crash at Start-up: Xorg Xubuntu 22.04 64bit"
date: 2024-01-11
forum: Desktop Environments
---

### Post by elgato-sad on 2024-01-11
Hello, 
I've been using Xubuntu 22.04 for a few months now, and I just started using linux, so I'm not very familiar with how to deal with crashes. 
Recently, every time after I log in I get a "System Problem" notification. At first I just reported it, but it's getting annoying so I went and checked the** /var/crash** and tried to read the** _usr_lib_xorg_Xorg.0.crash** file. So apparently the problem has something to do with **/usr/lib/xorg/Xorg** and **/var/run/lightdm/**. I've searched everywhere, it seems like many people have this issue, but everyone decided to just... live with it? Since it doesn't really have any catastrophic impact on the overall system (as far as I know...)
Another user created a [thread]("https://ubuntuforums.org/showthread.php?t=2445372") 3 years ago with EXACTLY the same problem, but I didn't saw any solution to it ... 

Again, I'm just starting my linux journey, so if anyone has an explanation for this issue, it would be much appreciated! 

Anyway, here is (some of) the content of the crash file (I cut off some parts from ProcMaps):

```

ProblemType: Crash
Architecture: amd64
Date: Thu Jan 11 17:27:15 2024
DistroRelease: Ubuntu 22.04
ExecutablePath: /usr/lib/xorg/Xorg
ExecutableTimestamp: 1702430913
ProcCmdline: /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
ProcCwd: /
ProcEnviron: PATH=(custom, no user)
ProcMaps:
 55a21e68c000-55a21e6cc000 r--p 00000000 103:08 1187079                   /usr/lib/xorg/Xorg
 55a21e6cc000-55a21e874000 r-xp 00040000 103:08 1187079                   /usr/lib/xorg/Xorg
 55a21e874000-55a21e8ed000 r--p 001e8000 103:08 1187079                   /usr/lib/xorg/Xorg
 55a21e8ee000-55a21e8f2000 r--p 00261000 103:08 1187079                   /usr/lib/xorg/Xorg
 55a21e8f2000-55a21e8fd000 rw-p 00265000 103:08 1187079                   /usr/lib/xorg/Xorg
 55a21e8fd000-55a21e93b000 rw-p 00000000 00:00 0 
 55a21f3d8000-55a21f42e000 rw-p 00000000 00:00 0                          [heap]
 7f2bcbae0000-7f2bcbae6000 r--p 00000000 103:08 1313796                   /usr/lib/xorg/modules/drivers/modesetting_drv.so
  ...
 7f2bcbb00000-7f2bcbb02000 r--p 00000000 103:08 1205227                   /usr/lib/x86_64-linux-gnu/libffi.so.8.1.0
  ...
 7f2bcbb0d000-7f2bcbb11000 r--p 00000000 103:08 1205213                   /usr/lib/x86_64-linux-gnu/libexpat.so.1.8.7
  ...
 7f2bcbb3e000-7f2bcbb45000 r--p 00000000 103:08 1206259                   /usr/lib/x86_64-linux-gnu/libwayland-server.so.0.20.0
  ...
 7f2bcbb54000-7f2bcbb57000 r--p 00000000 103:08 1205301                   /usr/lib/x86_64-linux-gnu/libgbm.so.1.0.0
  ...
 7f2bcbb65000-7f2bcbb67000 r--p 00000000 103:08 1205168                   /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
  ...
 7f2bcbb74000-7f2bcbb82000 r--p 00000000 103:08 1313284                   /usr/lib/xorg/modules/drivers/radeon_drv.so
  ...
 7f2bcbbee000-7f2bcbbf9000 r--p 00000000 103:08 1206324                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
  ...
 7f2bcbc18000-7f2bcbc31000 r--p 00000000 103:08 1182606                   /usr/lib/x86_64-linux-gnu/libX11.so.6.4.0
...
 7f2bcbd58000-7f2bcbd5b000 r--p 00000000 103:08 1204632                   /usr/lib/x86_64-linux-gnu/libGLX.so.0.0.0
  ...
 7f2bcbd7c000-7f2bcbd8c000 rw-p 00000000 00:00 0 
 7f2bcbd8c000-7f2bcbdcc000 r--p 00000000 103:08 1204637                   /usr/lib/x86_64-linux-gnu/libGLdispatch.so.0.0.0
  ...
 7f2bcbe3c000-7f2bcbe44000 rw-p 00000000 00:00 0 
 7f2bcbe44000-7f2bcbe87000 r--p 00000000 103:08 1204626                   /usr/lib/x86_64-linux-gnu/libGL.so.1.7.0
  ...
 7f2bcbeca000-7f2bcbecb000 rw-p 00000000 00:00 0 
 7f2bcbece000-7f2bcbed0000 r--p 00000000 103:08 1314733                   /usr/lib/xorg/modules/libfbdevhw.so
  ...
  ...
 .....
 7ffcfa255000-7ffcfa276000 rw-p 00000000 00:00 0                          [stack]
 7ffcfa34a000-7ffcfa34e000 r--p 00000000 00:00 0                          [vvar]
 7ffcfa34e000-7ffcfa350000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 --xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:    Xorg
 Umask:    0022
 State:    S (sleeping)
 Tgid:    837
 Ngid:    0
 Pid:    837
 PPid:    801
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    64
 Groups:     
 NStgid:    837
 NSpid:    837
 NSpgid:    837
 NSsid:    837
 Kthread:    0
 VmPeak:       19380 kB
 VmSize:       19380 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:        8960 kB
 VmRSS:        8960 kB
 RssAnon:        1280 kB
 RssFile:        7680 kB
 RssShmem:           0 kB
 VmData:        1840 kB
 VmStk:         132 kB
 VmExe:        1696 kB
 VmLib:        9288 kB
 VmPTE:          80 kB
 VmSwap:           0 kB
 HugetlbPages:           0 kB
 CoreDumping:    1
 THP_enabled:    1
 untag_mask:    0xffffffffffffffff
 Threads:    1
 SigQ:    25/23003
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    000000000a392000
 SigIgn:    0000000000001000
 SigCgt:    00000000418066cf
 CapInh:    0000000000000000
 CapPrm:    000001ffffffffff
 CapEff:    000001ffffffffff
 CapBnd:    000001ffffffffff
 CapAmb:    0000000000000000
 NoNewPrivs:    0
 Seccomp:    0
 Seccomp_filters:    0
 Speculation_Store_Bypass:    thread vulnerable
 SpeculationIndirectBranch:    conditional enabled
 Cpus_allowed:    ffff
 Cpus_allowed_list:    0-15
 Mems_allowed:    00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    893
 nonvoluntary_ctxt_switches:    9
Signal: 6
Uname: Linux 6.5.0-14-generic x86_64
UserGroups:

```

---

### Post by Holger_Gehrke on 2024-01-11
Unless I misread your post, what you encounter isn't actually repeating crashes but one crash. There's a problem with the crash-reporter which will under certain circumstances not remove a report but instead report it again and again, usually once after each subsequent login. The work-around consists of simply doing what the crash reporter should have done after telling you about the crash: delete the *.crash files in /var/crash.

I've encountered X crashes quite a few times, usually involving hardware accelerated video playback on damaged or malformed files. The hardware gets into states the driver doesn't expect and can't recover from and then the whole house of cards comes down ... So it's probably not Xorg but the graphics driver that's the problem. Since I configured my video player (mpv) not to use hardware acceleration by default the number of crashes has gone down to nothing.

And a few hints in case of a GUI crash: often the rest of the system is still fine. Try switching to a virtual terminal using ctrl-alt and one of the function keys and signing into the system. From a VT you can then proceed to do a controlled shutdown with 'sudo shutdown now'. If its not possible to reach a VT you can still try the '[Magic SysRQ key]("https://en.wikipedia.org/wiki/Magic_SysRq_key")'. The keys to hit after Alt-SysRq are R (reset the keyboard) E (send sigterm to all processes) I (send sigkill to all processes) S (sync all filesystems) U (remount all filesystems in read-only mode) B (reboot). Leave a bit of time after each key for the system to do the function. This is a lot better than doing an uncontrolled shutdown by holding the power button since it will write out all cached data and put the file systems in a consistent state.

Holger

---

