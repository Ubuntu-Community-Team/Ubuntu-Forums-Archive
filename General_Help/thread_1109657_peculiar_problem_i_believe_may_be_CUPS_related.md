---
title: "peculiar problem i believe may be CUPS related"
date: 2009-03-29
forum: General Help
---

### Post by bilmas on 2009-03-29
a week ago or so i tried configuring my brother ql-500 label printer and ubuntu recognized it initially and i suppose installed something to be used as a driver

everytime thereafter all updates would read an error due to the qlcupswrapper which had been installed in an attempt to get the label printer working so i looked into it and uninstalled it last night

today before work i shut my computer off and when i got home it would power up but there would be no display on the monitor and the computer certainly didn't seem to be working properly.  no beeps to indicate that anything was working.  i looked up similar problems online and they all seemed to stem from something specific but nothing was anything like my problem.  the solutions i had seen all suggested that it might be possible to reset the cmos by opening the tower and finding the appropriate switch on the motherboard.  i was definitely considering it an option but i wanted to wait before i did anything like that.  i turned the computer on again to see if anything had changed and as nothing i had i left it and went downstairs.

i was downstairs for about three hours and i just came back up to find that the computer had eventually booted itself up.  i'm not sure if i'd be safe restarting again but for now i'm going to keep the system running.  i did see a notice to update the os, however, and i clicked to do so.  while it built dependency trees it notified me that the software index is broken:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

so i followed those instructions and ql500cupswrapper was again mentioned:

```
david@david-desktop:~$ sudo apt-get install -f
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsilc-1.1-2 fglrx-kernel-source
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ql500cupswrapper
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 135418 files and directories currently installed.)
Removing ql500cupswrapper ...
/var/lib/dpkg/info/ql500cupswrapper.postrm: 4: /etc/init.d/cupsys: not found
dpkg: error processing ql500cupswrapper (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 ql500cupswrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@david-desktop:~$ 

```

i do notice that my colours also seem to be a bit off.  off-white rather than white.

i know this is probably very specific but maybe there is something familiar to somebody?

thanks in advance!
david

---

### Post by cariboo on 2009-03-29
I would suggest you use Synaptic to fix the broken package. Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

Jim

---

### Post by bilmas on 2009-03-29
do i have to select any packages when fixing broken package or is it a general fix?

---

### Post by bilmas on 2009-03-29
hrm i still don't seem to be having any luck. i click in synaptic to fix broken packages and it says that it successfully repaired broken dependencies but every update i try to do i get this:

```
E: ql500cupswrapper: subprocess post-removal script returned error exit status 127

```

---

### Post by todak on 2009-03-29
Perhaps [this]("http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html") may be of help.

---

### Post by bilmas on 2009-03-29
thanks for the link

i followed the instructions and all the files already contained the line #/bin/sh without the '-e'

still stuck

---

### Post by bilmas on 2009-03-30
any ideas from the night crew?

---

