---
title: "acpid error"
date: 2008-12-27
forum: General Help
---

### Post by wbrokow1 on 2008-12-27
```
Setting up acpid (1.0.4-5ubuntu9.1) ...
 * Stopping Hardware abstraction layer hald                                                               [ OK ] 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)
woody@woody-desktop:~$ 
```

Any ideas on why I am getting this error?
I am using Hardy Heron8.04

Thanks for any help

---

### Post by 67GTA on 2008-12-27
Open a terminal and run ```
sudo dpkg --configure -a
``` Hopefully that will get it moving.

---

### Post by wbrokow1 on 2008-12-27
```
woody@woody-desktop:~$ sudo dpkg --configure -a
Setting up acpid (1.0.4-5ubuntu9.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
woody@woody-desktop:~$ 
```

These are the results.
Thanks, if you can help.

---

### Post by 67GTA on 2008-12-27
Try stopping acpid, and then reconfiguring. The fact that it may be running could be stopping the install script.
```
sudo /etc/init.d/acpid stop
``````
sudo dpkg --configure acpid
```

---

### Post by wbrokow1 on 2008-12-27
```
woody@woody-desktop:/etc/apt$ sudo /etc/init.d/acpid stop
 * Stopping ACPI services...                                             [ OK ] 
woody@woody-desktop:/etc/apt$ sudo dpkg --configure acpid
Setting up acpid (1.0.4-5ubuntu9.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
```

I still get this.

Thanks for talking me through this.

---

### Post by 67GTA on 2008-12-27
I found a bug report for this. This is a weird problem. Maybe try removing/reinstalling. If this doesn't work, try dropping to runlevel 3 and running these again.

```
sudo /etc/init.d/acpid stop
```

```
sudo apt-get purge acpid
```

```
sudo apt-get install acpid
```

---

### Post by wbrokow1 on 2008-12-27
it didn't work.

how do drop to run level 3?

Thanks,
Walter

Ok I set the runlevel to 3.

It still didn't work.

Anything else?

I really appreciate the help.
THanks,

---

### Post by 67GTA on 2008-12-27
Did apt-get give an error when you tried to purge acpid?

---

### Post by wbrokow1 on 2008-12-27
No it did not give an error.
Thanks

---

### Post by wbrokow1 on 2008-12-27
```
woody@woody-desktop:~$ sudo apt-get purge acpid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  acpid*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169213 files and directories currently installed.)
Removing acpid ...
 * Stopping ACPI services...                                                                                                           [ OK ] 
Purging configuration files for acpid ...
woody@woody-desktop:~$ sudo apt-get install acpid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  acpid
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/29.1kB of archives.
After this operation, 180kB of additional disk space will be used.
Selecting previously deselected package acpid.
(Reading database ... 169194 files and directories currently installed.)
Unpacking acpid (from .../acpid_1.0.4-5ubuntu9.1_i386.deb) ...
Setting up acpid (1.0.4-5ubuntu9.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)
woody@woody-desktop:~$ 

```

---

### Post by 67GTA on 2008-12-27
I'm out of ideas. Just one more shot in the dark, but write all of these commands down so you can use them later. Then boot into recovery mode and run them one at a time in this order. At your grub screen where it shows the kernel lines, choose the second line. It should say recovery or safe mode somewhere in the line. A dialog will pop up asking you what to do. Choose "Drop to a root shell". Then give your root password to enter the commands. You need to be sure you have set up the root password first if you haven't already. You can do that through Menu>System>Administration>Users and Groups.

sudo /etc/init.d/acpid stop
sudo /etc/init.d/hal stop
sudo apt-get purge acpid
sudo apt-get clean
sudo apt-get update
sudo apt-get install acpid

---

### Post by djsong on 2009-02-18
Check this out
[https://bugs.launchpad.net/debian/+source/acpid/+bug/154887](https://bugs.launchpad.net/debian/+source/acpid/+bug/154887)

> This is claimed to be fixed in Debian (since 1.0.6-14), which needs to be merged.

I'm waiting for the update. (Yet I'm not using custom kernel but I'm having same problem. 2.6.24-23-server)

---

### Post by Crash54 on 2009-03-02
You might want to check out the writeup I put in:

[http://ubuntuforums.org/showthread.php?p=6487098&highlight=reference+thread](http://ubuntuforums.org/showthread.php?p=6487098&highlight=reference+thread)


Basically what I found is there was a script in my system related to the acpid operation which had a deprecated usage of the update-rc.d command.  The format it used is now no longer supported and caused the exact same lines of error messages that you indicate.

---

### Post by freakalad on 2009-04-29
Yip. Getting the same issue on my Hardy 64.

Tried all instructions as detailed in this thread (and a few other, just to be sure).
I've even tied building & installing [from source]("http://sourceforge.net/project/showfiles.php?group_id=33140"), and from manually installing the [.deb file]("http://archive.ubuntu.com/ubuntu/pool/universe/a/acpi/acpi_1.2-1ubuntu1_amd64.deb")

no dice

likely a bug...

---

