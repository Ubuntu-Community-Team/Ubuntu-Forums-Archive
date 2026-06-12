---
title: "kxdocker crashes on Feisty"
date: 2007-05-02
forum: Desktop Environments
---

### Post by pferrel on 2007-05-02
I installed kxdocker using synaptic from the feisty default repositories and get the run error listed below.  I have also tried getting the sources and compiling but get a make error on several of them.  I am running feisty on a new instalation with gnome and kde installed.

```
pferrel@pat-x1000:~/Desktop/kxdocker/kxdocker-configurator-1.0.2$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
DCOP aborting call from 'anonymous-9737' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.

[2]-  Exit 255                kxdocker

```

Also I have tried the instruction Martin Du Plooy left [here]("http://ubuntuforums.org/showthread.php?t=395682&highlight=kxdocker")  I can get through the apt-get steps so I should have all of the libraries installed but cannot compile the configurator.  In any case I get the above message when I run kxdocker.

Has anyone gotten kxdocker running on Feisty?

---

### Post by jiminycricket on 2007-05-03
This bug, post that you have the same problem too: [https://bugs.launchpad.net/bugs/105423](https://bugs.launchpad.net/bugs/105423)

I can't get kooldock to work without graphical glitches either: [https://bugs.launchpad.net/ubuntu/+source/kooldock/+bug/111152](https://bugs.launchpad.net/ubuntu/+source/kooldock/+bug/111152)

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

