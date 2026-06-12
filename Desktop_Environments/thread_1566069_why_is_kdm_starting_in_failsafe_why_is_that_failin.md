---
title: "why is kdm starting in failsafe? why is that failing?"
date: 2010-09-01
forum: Desktop Environments
---

### Post by albertz on 2010-09-01
Hi,

KDM always seems to start the failsafe server, not the normal one. At least I don't see any logs from a failed start attempt of the normal server (I checked /var/log/Xorg* and /opt/xorg/var/log/Xorg*). In the docs, I have read that KDM only starts the failsafe server if it fails to run X with the normal settings. Where/How can I find out why that fails?

Also, the failsafe server itself fails also. The log of that attempt:

```

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-24-generic-pae i686 
Current Operating System: Linux acompneu 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=599d9690-71d7-4f7d-a7aa-00e8c88fccf0 ro quiet splash
Build Date: 02 September 2010  01:54:20AM
 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Sep  2 03:37:23 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/opt/xorg/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/opt/xorg/lib/X11/fonts/misc/" does not exist.
	Entry deleted from font path.
(WW) The directory "/opt/xorg/lib/X11/fonts/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/opt/xorg/lib/X11/fonts/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/opt/xorg/lib/X11/fonts/Type1/" does not exist.
	Entry deleted from font path.
(WW) The directory "/opt/xorg/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/opt/xorg/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	
(==) ModulePath set to "/opt/xorg/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81ed900
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 1


Fatal server error:
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

```

Both problems might be because I have compiled Xorg myself. I actually have played a bit around with the Xorg Xserver sources and I want to test that, so I really want my self-compiled Xorg to work.

It also works already if I start it just by hand, i.e. for example just the command `Xorg :0 vt7` works perfect. This is why I am wondering if that is maybe still a problem on the Ubuntu/Debian side.

I hope someone can help.

Thanks,
Albert

---

### Post by clrg on 2010-09-02
Does this help you?

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/441653](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/441653)

---

### Post by albertz on 2010-09-02
Thanks for the reference! I think this is very related. It doesn't actually really help because there is still no good suggestion about how to fix this (only really ugly workaround which are so ugly/hacky that I don't even really like to try them out).

I have posted some further information on that bug report and also created a bug report for Xorg:
[https://bugs.freedesktop.org/show_bug.cgi?id=29975](https://bugs.freedesktop.org/show_bug.cgi?id=29975)

---

