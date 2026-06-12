---
title: "k3b error"
date: 2007-04-19
forum: Desktop Environments
---

### Post by naseem on 2007-04-19
hy I'm in feisty and I just installed k3b, since it was removed accidentaly (removing other kde staff) now when I lounch k3b this is what  I get after seeing the splash screen from k3b freezing and remaining on the screen:```
naseem@ramana:~$ k3bX Error: BadDevice, invalid or uninitialized input device 170  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
naseem@ramana:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model__NEC_DVD_RW_ND_4571A to device /dev/hda
/dev/hda resolved to /dev/hda

```

please help

---

### Post by taurus on 2007-04-19
Try removing it and reinstall it again to see if it pulls down all the dependencies.

```
sudo aptitude --purge remove k3b
sudo aptitude update
sudo aptitude install k3b
```

---

