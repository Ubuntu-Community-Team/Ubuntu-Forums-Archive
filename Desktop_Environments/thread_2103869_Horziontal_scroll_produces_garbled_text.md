---
title: "Horziontal scroll produces garbled text"
date: 2013-01-11
forum: Desktop Environments
---

### Post by trinacriax on 2013-01-11
Hi all,

Hope I'm not opening a duplicate thread.
I'm experiencing garbled/unreadable text in my system.

I noticed this issue on eclipse (attachment1), 
and I thought it was related to java.
Thus, I searched around and I found this
[thread for netbeans]("http://wiki.netbeans.org/FaqSolvingEditorGarbledText")

I applied the changes, reboot, but still there.
Then, I tried to reproduce the problem in a non-java
environment, thus I tried on gedit where I had the same issue (attachment2).
However, whenever I tried to capture the "screen", 
the garbled text in gedit become "crystal clear"
just after pressing PrtScn; weird, isn't it?
To get the "garbled" image in gedit,
I scroll the editor horizontally just after pressing PrtScn.

At this point, I think is some "driver" related issue,
or my xorg.conf is partially wrong... any idea?

System: Ubuntu 10.10 Maverick 64 bit Quad Core Q6600 RAM 8GB
Video: VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]
I installed AtiDriver from amd website: "amd-driver-installer-12.6-legacy-x86.x86_64", not from packages.

I have two monitors, multi-mode (no clone) in virtual resolution.

Update: When screen is locked and I enter a wrong password,
the login window shakes and the test is garbled as well;
unfortunately, I cannot take a screenshot.

```

$  Xorg -version

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux trinacria 2.6.35-32-generic #68-Ubuntu SMP Tue Mar 27 18:07:17 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-32-generic root=UUID=ab237190-af09-44c3-b0f5-081c63c9472b ro nomodeset quiet splash
Build Date: 20 October 2011  03:12:38PM
xorg-server 2:1.9.0-0ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```
```

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 2400 XT 
OpenGL version string: 3.3.11653 Compatibility Profile Context

```

---

