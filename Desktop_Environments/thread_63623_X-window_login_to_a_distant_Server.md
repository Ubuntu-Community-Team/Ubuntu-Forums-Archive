---
title: "X-window login to a distant Server ?"
date: 2005-09-08
forum: Desktop Environments
---

### Post by Typhoe on 2005-09-08
Hi,

this question has a lot of thread about it but I didn't find the answer for my problem.

I have 2 PC running Ubuntu 5.04
Let's call one Notebook, and the second Test.

Test has no display screen connected, but has a complete (and working) installation of ubuntu on it (GDM is running on). ssh daemon is running on it too (X11 forwarding activate).

From Notebook, I want to launch a new X-window session to connect to Test as if I was directly using it.

The 2 are on a lan and see each other perfectly (I can easily connect to Test from Notebook using ssh).

I tried:
sudo X :1 -query test

It launches a new X-window session on the ctrl+alt+F8 display but no gdm appears...
So I can't login on the Test PC...

Anyone know what I missed?

Thank you

My X-window log:
root@notebook:/home/typhoe # X :1 -query test

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux notebook 2.6.10-5-386 #1 Thu Aug 18 22:23:56 UTC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Aug 18 22:23:56 UTC 2005
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Sep  8 20:30:34 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Synaptics DeviceOff called

---

### Post by NutMonkey on 2005-09-08
Did you enable XDMCP in gdm on test?  It's disabled by default.

---

