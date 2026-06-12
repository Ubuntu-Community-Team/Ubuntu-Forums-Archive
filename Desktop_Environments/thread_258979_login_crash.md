---
title: "login crash"
date: 2006-09-16
forum: Desktop Environments
---

### Post by cottonwood on 2006-09-16
i installed aiglx last night using the howto found [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/") after which so, i rebooted, and now when i log in (under any session expept failsafe term) it will log me back out imediately.  it will flash the cmd with "login" and sometimes some of the startup stuff, and then willflash to the default ubuntu login screen. this sends me in circles.

when doing the recover boot, i can type startx and it will start w/no problem, so its something i must have done, and hopefully can fix.
if its needed, i'm running a compaq presario v3020us. intel graphis 9xx (not sure exactly).  kernal 2.6.15-26-686 (smp).  

is there a way to fix this?

---

### Post by cottonwood on 2006-09-16
ok. i fixed my problem. now however, since i don't want to start a new thread, i've it another wall.  when doing apt-get -f install (to fix errors) i get this:

> gareth@laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-aiglx
The following NEW packages will be installed:
  compiz-aiglx
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B/298kB of archives.
After unpacking 849kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-aiglx
Install these packages without verification [y/N]? y
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 1 during global destruction.
(Reading database ... 106116 files and directories currently installed.)
Unpacking compiz-aiglx (from .../compiz-aiglx_0.0.13-0gandalfn~dapper3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-aiglx_0.0.13-0gandalfn~dapper3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-aiglx_0.0.13-0gandalfn~dapper3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


what does it mean and how can a fix it?  apt-get clean doesn't help...

---

