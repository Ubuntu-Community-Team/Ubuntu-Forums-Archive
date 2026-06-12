---
title: "Make sure you have the 'universe' component enabled"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by ShaolinF on 2007-08-10
Hi guys,

I want to install kxdocker for 7.04 and it tells me to "Make sure you have the 'universe' component enabled". How can I do this ?

---

### Post by olejorgen on 2007-08-10
universe is a repsitory (or part of one)
A repository is a collection of software.

Search for "add repositories ubuntu feisty" or something

Also see: [http://ubuntuguide.org/index.php?title=Ubuntu:Feisty](http://ubuntuguide.org/index.php?title=Ubuntu:Feisty)

---

### Post by onestep on 2007-08-10
Click on "System" -> "Administration" -> "Software Sources".

On the "Ubuntu Software" tab look for the line that contains "(universe)". Make sure the check box next to that line is checked.

---

### Post by ShaolinF on 2007-08-10
Thanks guys. Ok, I'm trying to install kxdocker onto my 32bt 7.04 setup and its not working. Here is the output on terminal:

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

### Post by xdefconx on 2008-01-08
How to "Make sure you have the 'universe' component enabled":

What i know by using terminal edit /etc/apt/sources.list then add this:

add deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

:)

---

