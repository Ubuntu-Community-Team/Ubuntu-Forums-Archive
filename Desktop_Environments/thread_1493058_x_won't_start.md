---
title: "x won't start"
date: 2010-05-25
forum: Desktop Environments
---

### Post by lcslouis on 2010-05-25
i have a problem i can't start x the error is 
```
 startx


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux torrent 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: root=UUID=0d6a2f8e-06d8-484a-a444-02e3cca2fc4c ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 25 11:39:45 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) Failed to load module "dri" (module does not exist, 0)
(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed (libdri too old)
[dri] Disabling DRI.
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT2: INTERNAL_DAC2
  DFP1: INTERNAL_TMDS1
  DDC reg: 0x64
Dac detection success
finished output detect: 0
Dac detection success
Unhandled monitor type 0
finished output detect: 1
finished all detect
Dac detection success
Dac detection success
Unhandled monitor type 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable primary dac
disable primary dac
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 81620000
best_freq: 4294967295
best_feedback_div: 1
best_frac_feedback_div: 0
best_ref_div: 1
best_post_div: 1

Fatal server error:
Couldn't find valid PLL dividers


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

disable primary dac
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
```

please help me fix this i can't get x started i have removed x and gdm and reinstalled and it did not fix

---

