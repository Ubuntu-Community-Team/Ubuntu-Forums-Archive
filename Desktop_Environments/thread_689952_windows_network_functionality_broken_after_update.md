---
title: "windows network functionality broken after update"
date: 2008-02-06
forum: Desktop Environments
---

### Post by samandiriel on 2008-02-06
I have been happily using windows shares with my ubuntu install since Feisty with no issues (upgraded to Gutsy when it came out).  Today I suddenly cannot access the shares after rebooting.  The only thing I can thing of is that something came down the pipe in the automatic updates that broke it since I last rebooted a month or so ago that didn't kick in until I rebooted today.

I checked my dmesg, and found this suspicious:
[  417.078773]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[  417.078830]  CIFS VFS: cifs_mount failed w/return code = -110
[  794.410866]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[  794.410887]  CIFS VFS: cifs_mount failed w/return code = -110

But while I know CIFS is used to connect, that's the extend of my knowledge:(  So none of my network shares are working, and I cannot see my home Windows network in Places-Network anymore :(  Can anyone advise???

Thanks!
Tyler

UPDATE:  network functionality in general seems to be impaired...while I can ping Ubuntu from my Windows box, I can't ping my Windows box from Ubuntu.  Also, Remote Desktop and VNC both from Ubuntu to Windows no longer work (connection timed out error)...

UPDATE:  discovered root cause!  I had installed a wireless card in the windows PC, but had disabled it in the device manager.  However, this was enough to confuse windows so that no networking services like PING or RDP would respond.  Took card out...all was well!  God, how I hate that sort of thing...makes NO sense...

---

