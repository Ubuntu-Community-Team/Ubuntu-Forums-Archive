---
title: "Akonadi: no resource agents found"
date: 2010-03-12
forum: Desktop Environments
---

### Post by dentharg on 2010-03-12
Below you will find Akonadi errors I have.

I have completely removed all akonadi related dirs in my home directory. Did all the nepomuk upgrades as specified on wiki.

Still - no go. 

I can restart Akonadi server from Akonadi console after logging in and it heals the situation but every single time I log in
I have this nasty report of failed Akonadi startup.

Any thoughts?

Thanks!


Akonadi Server Self-Test Report
===============================

Test 4:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file &apos;<a href='/home/marcin/.local/share/akonadi/db_data/mysql.err'>/home/marcin/.local/share/akonadi/db_data/mysql.err</a>&apos; contains errors.

File content of '/home/marcin/.local/share/akonadi/db_data/mysql.err':
100312 20:45:06 [Note] Plugin 'FEDERATED' is disabled.
100312 20:45:07  InnoDB: Started; log sequence number 0 2717594
100312 20:45:08 [Warning] Can't open and lock time zone table: Table 'mysql.time_zone_leap_second' doesn't exist trying to live without them
100312 20:45:08 [ERROR] Can't open and lock privilege tables: Table 'mysql.servers' doesn't exist
100312 20:45:08 [ERROR] Cannot open mysql.db
100312 20:45:08 [ERROR] Cannot open mysql.user
100312 20:45:08 [ERROR] Cannot open mysql.event
100312 20:45:08 [ERROR] Event Scheduler: An error occurred when initializing system tables.
100312 20:45:08 [Note] /usr/sbin/mysqld-akonadi: ready for connections.
Version: '5.1.37-1ubuntu5-log'  socket: '/home/marcin/.local/share/akonadi/db_misc/mysql.socket'  port: 0  (Ubuntu)
Test 14:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 16:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/marcin/.local/share/akonadi/akonadiserver.error.old'>/home/marcin/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/marcin/.local/share/akonadi/akonadiserver.error.old':
Control process died, committing suicide! 


Test 17:  ERROR
--------

Current Akonadi control error log found.
Details: The Akonadi control process did report error during startup into <a href='/home/marcin/.local/share/akonadi/akonadi_control.error'>/home/marcin/.local/share/akonadi/akonadi_control.error</a>.

File content of '/home/marcin/.local/share/akonadi/akonadi_control.error':
Unable to register service as org.freedesktop.Akonadi.Control Maybe it's already running? 
"[
0: /usr/bin/akonadi_control(_Z11akBacktracev+0x35) [0x805bca5]
1: /usr/bin/akonadi_control [0x805c176]
2: [0x38b400]
3: [0x38b422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x3b64d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x3b9932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xa0b32c]
7: /usr/bin/akonadi_control(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x805d1f4]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x8e) [0xaa3f7e]
9: /usr/lib/libQtCore.so.4 [0xab7b85]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3d) [0xab909d]
11: /usr/bin/akonadi_control(main+0x424) [0x8070d24]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x3a2b56]
13: /usr/bin/akonadi_control [0x8057871]
]
"

---

### Post by pcornelissen on 2010-04-19
I'm having the same problem. "Funny" thing is that it works on another machine that is on lucid too...

---

### Post by dentharg on 2010-04-19
I've put Lucid on VirtualBox (clean install). Works fine.
Update from my Karmic - no go.

---

### Post by cosmicbuff on 2010-04-20
same here. started off fine in lucid beta, but update broke it.

---

### Post by Maximus_ARNP on 2010-05-20
I have been able to solve this problem as follows:

> 
Add following line to the file **.bushrc** in **/home/USERNAME** folder:
[QUOTE]
export XDG_DATA_DIRS="/opt/kde/share/akonady/agents:$XDG_DATA_DIRS"

**Reference**: [http://forum.kde.org/viewtopic.php?f=20&t=85072](http://forum.kde.org/viewtopic.php?f=20&t=85072)
[/QUOTE]

Restart your computer.

It worked for me.

Sincerely.

Raj.

---

### Post by emaxx on 2010-06-01
Oh yes, very smart: you point to "/opt/kde ...", a directory that doesn't exist at all on usual installations ...

This seems to match all the other akonady-<snip>, which is just a big <snip>!

---

### Post by sphoid on 2010-07-15
In kubuntu, the actual folder you want is /usr/share/akonadi/agents

---

### Post by skfin on 2010-07-19
And actually I think that the file you need to edit is .bashrc not .bushrc ;)

---

