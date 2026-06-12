---
title: "Virtual TTY X server crash"
date: 2009-02-27
forum: Desktop Environments
---

### Post by XanTrax on 2009-02-27
I posted this on launchpad under the bug I found but it seems to be about a year old so I do not know if anyone will get to it ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/30395](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/30395)).  Heres my issue:

In a virtual TTY (ctrl+alt+[f1 => f7]) I am trying to enable an X session via the startx command. Whether I do it in a virtual TTY or in a gnome-terminal/xterm console, the output is always the same.  Once I switch out of that TTY the X server (on that TTY) seems to crash or at least the desktop disappears.  I have to do an interrupt (ctrl+c) and wait for the X server to stop or kill the Xorg process on that TTY to get back to my console prompt.

I start the X server with on the TTY with:

```

startx -- :1

```

This output is the same whether I run the above command in a virtual TTY or in a gnome-terminal/xterm console from the primary TTY (ctrl+alt+f7).  The output below is displayed when I:

1. Press "Ctrl+Alt+f1" to go into Virtual TTY 1
2. Type "startx :1"
3. Gnome or fluxbox or whichever Desktop Environment I have specified is loaded
4. I switch from TTY 1 (ctrl+alt+f1)  back to the primary TTY 7 (ctrl+alt+f7) without a problem
5. Upon switching back to TTY 1 (ctrl+alt+f1) the output below is displayed

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux kozler-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
 Before reporting problems, check http://wiki.x.org
 to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
 (++) from command line, (!!) notice, (II) informational,
 (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Feb 26 16:02:55 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No input driver/identifier specified (ignoring)
(EE) config/hal: NewInputDeviceRequest failed
BScreen::BScreen: managing screen 0 using visual 0x23, depth 24
apps file failure
^C
waiting for X server to shut down XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 41767 requests (41764 known processed) with 0 events remaining.

```

The ^C is where I do the interrupt so it can shutdown.  There is nothing in .Xsession-errors.  My Xorg.log is attached as well as my system specs are below.

System Information
> 
SYSTEM INFORMATION
 Running Ubuntu Linux, the Ubuntu 8.10 (intrepid) release.
 GNOME: 2.24.1 (Ubuntu 2008-10-24)
 Kernel version: 2.6.27-11-generic (#1 SMP Thu Jan 29 19:24:39 UTC 2009)
 GCC: 4.3.2 (i486-linux-gnu)
 Xorg: unknown (24 October 2008 08:00:16AM)
 Hostname: kozler-laptop
 Uptime: 0 days 0 h 6 min
        GenuineIntel, Intel(R) Core(TM)2 CPU T7600 @ 2.33GHz
       Total memory: 2023 MB

GRAPHIC CARD
 VGA controller
  ATI Technologies Inc M56GL [Mobility FireGL V5250]


Thank you for any help.

---

### Post by XanTrax on 2009-02-28
Hate to do this but its kind of important...

bump

---

