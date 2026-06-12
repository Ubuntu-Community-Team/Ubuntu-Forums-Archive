---
title: "Desktop crashes and kicks user back to graphical log-in screen on start GNU Emacs w/X"
date: 2013-06-06
forum: Desktop Environments
---

### Post by christopherbalz on 2013-06-06
$ uname -a
Linux foobar-1 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Distro is Ubuntu 12.04 LTS

More detail on the problem: Same thing happens on start VirtualBox and on start Skype.  All these programs used to work before I switched to the proprietary NVidia driver (which I did in order to get support for multiple concurrent graphical user desktops).  Now, switching back to the open-source one does not help.
  
Happens on Gnome desktop as well as Unity desktop.  Changing users does not affect the issue.  I have used `sudo unity --reset` and that seems to work, although it hangs on 'run key'.  I have also used the Compiz dialog to reset to defaults.  No indication of any issue in dmesg or in X.org logs.

It's bad when you can't start Gnu Emacs on your Linux box's graphical desktop.

---

### Post by christopherbalz on 2013-06-08
Although the crash occurs as well with VirtualBox and Skype, the Gnu Emacs (with X) crash log might help.  A key line seems to be:  'kill () from /lib/x86_64-linux-gnu/libc.so.6', triggered upstream by this: '_XIOError () from /usr/lib/x86_64-linux-gnu/libX11.so.6'.  

from: '/var/crash/_usr_bin_emacs23-x.10' : 

ProblemType: Crash
Architecture: amd64
CrashCounter: 1
. . . 
 7fce173e0000-7fce173e2000 rw-p 00023000 08:01 8007527                    /lib/x86_64-linux-gnu/ld-2.15.so
 7fff0df0d000-7fff0df36000 rw-p 00000000 00:00 0                          [stack]
 7fff0df80000-7fff0df81000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

ProcStatus:
 Name:  emacs23
 State: S (sleeping)
 Tgid:  6757
 . . . 
Signal: 6
Uname: Linux 3.2.0-45-generic x86_64
. . .
UserGroups: adm admin audio cdrom dialout floppy fuse lpadmin netdev plugdev powerdev sambashare scanner tomcat6 video
CoreDump: base64
 H4sICAAAAAAC/0NvcmVEdW1wAA==
. . . 
Disassembly:
 => 0x7fce1275e707 <kill+7>:    cmp    $0xfffffffffffff001,%rax
    0x7fce1275e70d <kill+13>:   jae    0x7fce1275e710 <kill+16>
. . . 
InstallationMedia: Ubuntu 10.04 LTS "Lucid Lynx" - Release amd64 (20100429)
MarkForUpload: True
NonfreeKernelModules: nvidia
Package: emacs23 23.3+1-1ubuntu9.1
PackageArchitecture: amd64
ProcVersionSignature: Ubuntu 3.2.0-45.70-generic 3.2.44
Registers:
 rax            0x0     0
 rbx            0x6     6
 rcx            0xffffffffffffffff      -1
. . . 
SourcePackage: emacs23
Stacktrace:
 #0  0x00007fce1275e707 in kill () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 #1  0x00000000004e3bdb in ?? ()
. . . 
 #9  0x00007fce145752be in _XIOError () from /usr/lib/x86_64-linux-gnu/libX11.so.6
 No symbol table info available.
 #10 0x00007fce1457324b in _XReply () from /usr/lib/x86_64-linux-gnu/libX11.so.6
 No symbol table info available.

---

### Post by christopherbalz on 2013-06-08
Link to more complete crash log: [http://pastebin.com/cWftnENy](http://pastebin.com/cWftnENy)

---

### Post by christopherbalz on 2013-06-08
VirtualBox, Skype, and Gnu Emacs (running in X mode) all crash my standard, up-to-date Ubuntu 12.04 LTS desktop (under all Gnome and Unity desktops).  Link to complete '/var/crash/_usr_bin_emacs23-x.1000.crash' crash log: [http://pastebin.com/cWftnENy](http://pastebin.com/cWftnENy)  

At least, Gnu Emacs and Virtual Box should run!  There are more programs that crash the desktop as well.

Nothing interesting in dmesg or the system logs.

Changing users does not affect the issue. I have used `sudo unity --reset` and that seems to work, although it hangs on 'run key'. I have also used the Compiz dialog to reset to defaults. No indication of any issue in dmesg or in X.org logs.

$ uname -a 
Linux foobar-1 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by christopherbalz on 2013-06-08
When the crash happens, the entire desktop shuts down, the screen goes black, and the user is kicked back to the original graphical log-in screen.

---

### Post by matt_symes on 2013-06-09
threads merged

---

### Post by matt_symes on 2013-06-09
Create a bug report an Launchpad.

---

### Post by lite1979 on 2013-06-11
I'm so glad I found this thread! I'm experiencing the same crash. At first I was too impatient to wait for it to kick me back to the desktop login, and I would have to press the reset button or the power button to restart, but if I wait a minute, my screen returns to the graphical unity login. This has been happening to me when using firefox...

AMD Athlon 64 x2 4800+
4GB RAM
12.04 LTS 3.5.0-32-generic
160GB Sata HD (129GB free)
NVIDIA GT 240 1GB PCIe, driver 319.17

---

### Post by christopherbalz on 2013-06-15
Uninstalling xfs, for example by simply using Synaptic (search on 'xfs', and do 'Remove' (but not 'Remove Completely'), worked for me on Ubuntu 12.04 LTS all-up-to-date as of now.  

I found this solution by following the instructions at [https://help.ubuntu.com/community/ReportingBugs#Reporting_a_Bug](https://help.ubuntu.com/community/ReportingBugs#Reporting_a_Bug) , including the work-around to the bug-reporting mechanism feature that is, rather, a horrible bug ( [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/994921](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/994921) ).  

How I found the solution: When, after several months of thinking my problem report was being uploaded, I thought to make sure it was being uploaded, I found at the instructions mentioned above that indeed, the "uploading" or "reporting of the problem" was only a mirage (the appropriately-misleading dialogs were there, but the actual work was not happening under the hood).  

So once I actually had the bug reporting working again, as it used to before the "feature" was inflicted upon the community, I found other bugs on Launchpad because the Launchpad website found several others with the same title as my auto-uploaded, auto-titled one had.  Those bug reports contained the work-around fix, to remove the xfs package.  The bug reports are: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/738526](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/738526) and [https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/795373](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/795373) .  **If this issue affects you, please vote on those bugs (link a few inches down from the top of those bug report pages, at left), and if you also run an LTS version of Ubuntu, please vote on [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/994921](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/994921)** .

This issue of unrelated bugs layering on top of one another forms a nearly impenetrable shield to those who are not able to dedicate large amounts of time to debugging Ubuntu.

---

