---
title: "KDM crashes on boot"
date: 2007-12-01
forum: Desktop Environments
---

### Post by Zorael on 2007-12-01
When booting, KDM tries to start, almost succeeds, then crashes. The GUI loads properly in the proper resolution, with the proper mouse cursor, but never gets to the actual login box. It throws me  to tty8, forcing me to switch to a usable console, log in, killall kdm, and then start it manually. *Then* it works.

I can't pinpoint when this started, but it sure worked fine up until somewhere mid-November.

What log files should I consult? Casually skimming over /var/log/kdm.log and /var/log/Xorg.0.log I don't see any glaring error messages, but then again, I don't know what to look for.

I *have* tampered with the system services runlevels. kdm remains at "2, 3, 4, 5" though, which I understand is the proper setup?


Please help, it's borderline showstopper for me, and I don't want to reinstall again. :(

---

### Post by kellemes on 2007-12-01
- Have you upgraded to the latest KDM?
- /var/log/syslog could be interesting..
- Uninstall GDM if possible or at least... Delete (#-comment out) any reference to GDM in the runlevel of choice.. (I can't help you here since I'm using Archlinux myself, Arch handles runlevels differently)

---

### Post by Zorael on 2007-12-01
I neglected to mention, but if it's not obvious by this time, I'm running Kubuntu 7.10, backports repositories enabled.

> **kellemes said:**
> - Have you upgraded to the latest KDM?
- /var/log/syslog could be interesting..
- Uninstall GDM if possible or at least... Delete (#-comment out) any reference to GDM in the runlevel of choice.. (I can't help you here since I'm using Archlinux myself, Arch handles runlevels differently)

KDM: I haven't upgraded from any external sources outside of the official repositories, so unless there's been a backport update I don't remember, I have the version included in the Gutsy release.
```
zorael@azrael:~$ apt-cache policy kdm
kdm:
  Installed: 4:3.5.8-0ubuntu2
  Candidate: 4:3.5.8-0ubuntu2
  Version table:
 *** 4:3.5.8-0ubuntu2 0
        500 http://se.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
```

/var/log/syslog: I don't see anything glaring in there either, besides a warning provoked when I killed kdm manually..
```
Dec  1 13:56:52 azrael dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Dec  1 13:56:53 azrael dhclient: DHCPACK from 192.168.0.1
Dec  1 13:56:53 azrael avahi-daemon[8147]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Dec  1 13:56:53 azrael avahi-daemon[8147]: New relevant interface eth1.IPv4 for mDNS.
Dec  1 13:56:53 azrael avahi-daemon[8147]: Registering new address record for 192.168.0.4 on eth1.IPv4.
Dec  1 13:56:53 azrael dhclient: bound to 192.168.0.4 -- renewal in 42827 seconds.
Dec  1 13:56:54 azrael ntpdate[8589]: adjust time server 91.189.94.4 offset -0.000866 sec
**Dec  1 13:57:04 azrael kdm: :0[7681]: Abnormal termination of greeter for display :0, code 1, signal 0**
Dec  1 14:00:57 azrael NetworkManager: <info>  Updating allowed wireless network lists. 
Dec  1 14:00:57 azrael NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks.
```

GDM: I've never had GDM installed, since I run Kubuntu. And I don't see how this could cause the problem, since it starts properly, but crashes before it can get to the login screen.
```
zorael@azrael:~$ apt-cache policy gdm
gdm:
  Installed: (none)
  Candidate: 2.20.1-0ubuntu1
  Version table:
     2.20.1-0ubuntu1 0
        500 http://se.archive.ubuntu.com gutsy-updates/main Packages
     2.20.0-0ubuntu6 0
        500 http://se.archive.ubuntu.com gutsy/main Packages
```

---

### Post by Zorael on 2007-12-01
```
zorael@azrael:/etc/X11$ cat default-display-manager
/usr/bin/kdm
```

Perhaps if I completely removed KDM and installed it again? Though that will likely uninstall other packages included in the kdm "virtual" package, at a lack of better ways of explaining it.

I'm pretty sure I tried dpkg-reconfigure kdm. 95%. I'll restart now; then I'll know for sure.

---

### Post by Zorael on 2007-12-01
dpkg-reconfigure kdm didn't help.

But!

Examining kdm.log more thoroughly I notice an interesting tidbit.
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux azrael 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  1 20:12:20 2007
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
Atom 4, CARD32 4, unsigned long 4
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
**kdmgreet: cannot connect to X server :0**
Synaptics DeviceOff called
```

Cannot connect? Why? :(

---

