---
title: "Crash cause by viewing update details?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Roman27 on 2006-07-13
This is really weird, but just now I had 6 updates waiting for me.  One of them was "login".  I went to "Show details" on the "login" update and it blew me right out of X windows.  After a few seconds, I wound up at the logon screen again.  I did the same thing again; checked the updates and tried to show details on the login update.  This time my system froze solid.  I tried CTRL-ALT-BACKSPACE, but it had no effect.

After rebooting, I did the same thing.  First offence, it kicks you out of X Windows.  Second offence, it freezes solid.  The only error I could dig out was in /var/log/gdm/:0.log.3

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux dim8300 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 11 20:47:38 2006
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/bin/X [0x813bd9d]
3: /usr/bin/X [0x813e70e]
4: /usr/bin/X(Dispatch+0x19e) [0x8085d26]
5: /usr/bin/X(main+0x47c) [0x806e0a8]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d8dea2]
7: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting

```
Has anyone else had this issue?  It looks like the line 7 of the backtrace is talking about fonts.  Maybe the detail for that package had strange fonts in it or something?

By the way, installing the updates (without viewing the details) went fine without any errors.

---

### Post by DeathOnJuice on 2006-08-27
I am having a very similar problem, so I'm glad I found this by searching. Basically, when I go to one particular website in Firefox that has custom maps for a flash game called N, I get booted back to the login screen several times and then the system freezes solid, just like yours. I go to this site a lot, so it's a big problem. Generally, the problem happens when I close a tab in that website, although sometimes it's when I look at a map.

Here's the offending website: numa.notdot.net

Here's some more details about my problem: [http://www.ubuntuforums.org/showthread.php?p=1427171#post1427171](http://www.ubuntuforums.org/showthread.php?p=1427171#post1427171)

If anyone could help us, I'd be a happy man!

Edit: I found these errors in my ~/.xsession-errors. There were quite a few, but these have HTML in them, so could it be the problem? Where else should I look for errors?

```

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:10581): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files) 
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

```

---

### Post by DeathOnJuice on 2006-08-27
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-28
Bump.

---

### Post by DeathOnJuice on 2006-08-30
Bump.

---

### Post by DeathOnJuice on 2006-08-30
Bump.

---

### Post by DeathOnJuice on 2006-08-31
Bump.

---

### Post by DeathOnJuice on 2006-09-02
Bump.

---

