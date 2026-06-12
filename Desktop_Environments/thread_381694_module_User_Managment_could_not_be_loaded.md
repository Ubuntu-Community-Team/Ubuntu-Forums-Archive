---
title: "module User Managment could not be loaded"
date: 2007-03-11
forum: Desktop Environments
---

### Post by roflcopter on 2007-03-11
Um, when i try to run user managnemt through system settings i get an error.
When i try to run it in terminal, it says this:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
no user removed
Traceback (most recent call last):
  File "/usr/bin/userconfig", line 1711, in ?
    userconfigapp = UserConfigApp()
  File "/usr/bin/userconfig", line 275, in __init__
    self.__updateGroupList()
  File "/usr/bin/userconfig", line 515, in __updateGroupList
    self.__selectGroup(self.selectedgroupid)
  File "/usr/bin/userconfig", line 521, in __selectGroup
    lvi = self.groupidsToListItems[groupid]
KeyError

```

And one another question: how do i configure my soundcard? I have SB live 24bit and i can't set channels for the rear left/right speakers in alsamixer. only options i have are analog/front, analog/rear and analog/side(?)

---

