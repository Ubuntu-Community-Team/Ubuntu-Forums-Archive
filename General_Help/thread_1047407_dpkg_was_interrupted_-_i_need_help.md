---
title: "dpkg was interrupted - i need help"
date: 2009-01-22
forum: General Help
---

### Post by Jimsson on 2009-01-22
Today when i tried to update Ubuntu it checked for updates but when i clicked install this is what i got:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

So i rebooted but that changed nothing. When i looked in the synaptic package manager i got the same message! 

So what can i do to fix this? i don't know much about Linux overall so give me the easy advice please! ;)

---

### Post by overdrank on 2009-01-22
> **Jimsson said:**
> Today when i tried to update Ubuntu it checked for updates but when i clicked install this is what i got:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

So i rebooted but that changed nothing. When i looked in the synaptic package manager i got the same message! 

So what can i do to fix this? i don't know much about Linux overall so give me the easy advice please! ;)

Hi and have you tried to use the command given in the terminal ```
sudo dpkg --configure -a
```

---

### Post by Jimsson on 2009-01-22
this is what i got: 

```

jim@jim-desktop:~$ sudo dpkg --configure -a
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```
and it didn't fix the problem!

---

### Post by mgol on 2009-01-22
It seems it's just Ubuntu bug, see:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/dpkg/+bug/262451](https://bugs.launchpad.net/ubuntu/intrepid/+source/dpkg/+bug/262451)

---

### Post by oaqster on 2009-01-22
i had run into this a few months back when my laptop's battery died on me during installing a package.  not fully sure but i *think* i had done aptitude -reinstall of the package in question to resolve the issue. try that with the mysql-server or mysql-server-5.0 and see if that fixes the problem

therez also an option to remove a broken package in dpkg using the remove-reinstreq (looked through man)

- oaqster

---

