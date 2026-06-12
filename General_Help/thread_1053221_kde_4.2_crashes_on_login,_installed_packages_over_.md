---
title: "kde 4.2 crashes on login, installed packages over Ubuntu 8.10"
date: 2009-01-28
forum: General Help
---

### Post by dhazin on 2009-01-28
Here is short description of my actions:

0. I have Ubuntu 8.10 with  nvidia 7600GS; problem persists with
177.xx, 180.11 (from launchpad) and 180.25 drivers

1. I used following repository for kde 4.2:
deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
multiverse restricted universe

2. Installed kubuntu-desktop, selected kdm as a default display manager

3. Reboot

4. Login to kde fails, there are following lines in syslog:

Jan 29 00:33:05 dhazin kernel: [  464.893443] kded4[9823]: segfault at
0 ip 48be08a5 sp bf8be9d0 error 4 in
libQtGui.so.4.4.3[48a34000+8f5000]
Jan 29 00:33:05 dhazin kernel: [  464.985041] kcminit_startup[9827]:
segfault at 0 ip 48be08a5 sp bfd74f90 error 4 in
libQtGui.so.4.4.3[48a34000+8f5000]
Jan 29 00:33:05 dhazin kernel: [  465.107018] ksmserver[9829]:
segfault at 0 ip 48be08a5 sp bfeb5fd0 error 4 in
libQtGui.so.4.4.3[48a34000+8f5000]



Is this a known bug and can I do anything to workaround it? Should I
post bug report somewhere and if yes what information should I place
there?

---

### Post by dhazin on 2009-01-30
Here is my .xsession-errors:

Xsession: X session started for dhazin at &#1055;&#1090;&#1085; &#1071;&#1085;&#1074; 30 23:11:04 NOVT 2009
Setting IM through im-switch for locale=ru_RU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
kdostartupconfig4(7741) main: Running kdostartupconfig.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kded(7769): Communication problem with  "kded" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

kdeinit4: preparing to launch /usr/bin/kcminit_startup
kdeinit4: preparing to launch /usr/bin/ksmserver
<unknown program name>(7767)/ KStartupInfo::createNewStartupId: creating:  "dhazin;1233335466;389285;7767_TIME0" : "unnamed app"
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.

---

