---
title: "Cant install kxdocker in 7.04"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by ShaolinF on 2007-08-10
I'm trying to install kxdocker onto my 32bt 7.04 setup and its not working. Here is the output on terminal:

```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
DCOP aborting call from 'anonymous-23583' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.
```

---

### Post by ShaolinF on 2007-08-11
bump.

---

### Post by Chen Jun on 2007-09-05
I am facing same issue. :-(

---

### Post by Inxsible on 2007-09-05
First uninstall kxdocker and then go to your home folder and remove all configuration files related to kxdocker.

Then try and re-install.

---

### Post by Chen Jun on 2007-12-02
forgort about the kxdocker, try latest version of kooldock, it is much better and really cool.

---

