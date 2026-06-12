---
title: "X-Server Crash"
date: 2007-01-15
forum: Desktop Environments
---

### Post by cornish on 2007-01-15
I know this has been posted before but it never seems to apply to me.
X seems to crash randomly I can be opening up switfox or loading mplayer and it will just restart and take me back to the logon screen.

Can some one help I have pasted a copy of my log file for you to mull over

> X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux mark-desktop 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 15 21:09:45 2007
(==) Using config file: "/etc/X11/xorg.conf"
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Mon Jan 15 21:09:47 2007: 15270 X: client 2 rejected from local host
AUDIT: Mon Jan 15 21:09:47 2007: 15270 X: client 4 rejected from local host
AUDIT: Mon Jan 15 21:09:47 2007: 15270 X: client 3 rejected from local host
AUDIT: Mon Jan 15 21:09:47 2007: 15270 X: client 5 rejected from local host

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(XkbProcessKeyboardEvent+0x92) [0x8180ac2]
3: /usr/X11R6/bin/X(AccessXFilterPressEvent+0xd6) [0x81785a6]
4: /usr/X11R6/bin/X(ProcessKeyboardEvent+0xa0) [0x8180e20]
5: /usr/X11R6/bin/X(xf86eqProcessInputEvents+0x21d) [0x80e24ad]
6: /usr/X11R6/bin/X(ProcessInputEvents+0x29) [0x80c4c89]
7: /usr/X11R6/bin/X(Dispatch+0x72) [0x8086822]
8: /usr/X11R6/bin/X(main+0x485) [0x806e715]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d168cc]
10: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting


---

