---
title: "kde weird problem with focus and others"
date: 2007-11-06
forum: Desktop Environments
---

### Post by agent-s on 2007-11-06
so basically, I have suddenly been beset with a host of problems.

Here are the latest few actions I can  remember:
update to Kubuntu 7.10
removed all gnome stuff
remove & install koffice
install & remove deluge-torrent + dependencies

now:
-Knetworkmanager does not report any active devices (even though everything still works fine) (mentioned in another thread)
-Whenever I open Dolphin (or any other KDE dialog) it can take a while before I can do anything because it spends about 10 seconds on a widget gaining/losing focus
-it seems like the gnome systray is showing up in the kde panel, but when i mouse over it, it disappears behind the kde panel

Any help would be appreciated.  It doesn't seem like the KDE developers have enough time to look into it themselves.

---

### Post by Happy_Man on 2007-11-06
Yeah.... uh, I would recommend a fresh install over an upgrade any day. Quite honestly, there's just so much to do that Ubuntu can't handle all the dependencies and updating... so upgrades generally turn out to be crappy. B urn a fresh ISO of Kubuntu 7.10 and install that (after backing up everything you need/want, of course), and your problems will be solved. I only suggest this because it would be too much trouble for me, you, or anyone, for that matter, to go through and fix all these issues and any more that may crop up due to our fixing. :)

---

### Post by agent-s on 2007-11-07
Well I've solved the gnome systray problem (I think).

However, now I can't mount even my cd drive.

Here's the output of dmesg:

:~$ dmesg | tail
[121196.335653] ide: failed opcode was: unknown
[121196.336687] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[121196.336708] end_request: I/O error, dev hdc, sector 1024
[121196.336823] UDF-fs: No partition found (1)
[121196.415593] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[121196.415609] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[121196.415614] ide: failed opcode was: unknown
[121196.416310] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[121196.416324] end_request: I/O error, dev hdc, sector 64
[121196.416398] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

---

