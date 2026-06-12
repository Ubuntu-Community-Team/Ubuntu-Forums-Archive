---
title: "America's Army Crashes for No Reason...."
date: 2005-09-08
forum: Gaming &amp; Leisure
---

### Post by TristanMike on 2005-09-08
Well, I suppose not "no reason" because there is always a reason, but more like very unexpectedly. Anyway here's the error from the terminal```
tristan@ubuntu:~$ armyops
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.
tristan@ubuntu:~$
```Can anyone explain what this may mean? I don't know where to look for the "logfile". I've done some reading through google, but I don't really understand it. Can anyone help me please? And what does this code do```
xinit /$usr/local/games/armyops -- :1
```Well, I went ahead and typed it in, and my desktop appeared to reboot as I got the nVidia splash, but my screen went grey with an "X" for a cursor, and nothing else. I thought I lost my system but a quick "ctrl+alt+backspace" brought me out, back to the terminal, whew! So when I came back, this.....```
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux ubuntu 2.6.10-5-386 #1 Thu Aug 18 22:23:56 UTC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Aug 18 22:23:56 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Sep  8 01:30:34 2005
(==) Using config file: "/etc/X11/xorg.conf"

Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
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
AUDIT: Thu Sep  8 01:30:39 2005: 17288 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified


waiting for X server to begin accepting connections .
AUDIT: Thu Sep  8 01:30:41 2005: 17288 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Thu Sep  8 01:30:43 2005: 17288 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Thu Sep  8 01:30:45 2005: 17288 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Thu Sep  8 01:30:47 2005: 17288 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Thu Sep  8 01:30:49 2005: 17288 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.
tristan@ubuntu:~$

```was in the terminal. So what does this mean? Any help is greatly appreciated.

---

### Post by shakin on 2005-09-08
try running 'killall esd' and then run the game.

---

### Post by TristanMike on 2005-09-08
Thanks for the reply sir.  :) 

Ummm, ok, if you don't mind though, before I go and type in arbitary code in the terminal, why do you think the sound is causing the issue? I've never had a problem with sound so what leads you to believe this is the solution? The crashing is pretty random, sometimes it doesn't happen at all during a session, but yesterday for instance, it happened twice. Please elaborate.  :)

EDIT: Oh, and what does the "xinit...." line of code do?

---

### Post by TristanMike on 2005-09-11
Can anyone help? It is happening more frequently now.

---

