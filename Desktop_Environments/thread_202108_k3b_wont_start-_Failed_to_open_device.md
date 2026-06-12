---
title: "k3b wont start- Failed to open device"
date: 2006-06-22
forum: Desktop Environments
---

### Post by weijie90 on 2006-06-22
Hi,
i used apt to install k3b, but it wont start: 

```
k3bdi@di-desktop:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-di"
Link points to "/tmp/kde-di"
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
kbuildsycoca running...
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

```

Please help, thanks!

---

### Post by missmoondog on 2006-08-13
i get almost the same thing on one of my machines. i've posted replies to a few different thread here so far and have not gotten a reply to any of them yet. the major opcode in my error list is 146 though. k3b will start immediately, automatically upon rebooting after having tried to start it through kmenu or terminal.


edit:
here's my error message
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: Communication problem with k3b, it probably crashed.
desktop:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
ScimInputContextPlugin()

---

### Post by missmoondog on 2006-08-17
darn! can't get any responses to this?

---

### Post by missmoondog on 2006-08-18
have fixed my problem. did a clean install of ubuntu and graveman. burner works correctly now.

wonder what the issue was using kubuntu on this computer? everything pretty much worked right out of the box with kubuntu on my 6 other machines.

---

### Post by irie.stamp on 2007-06-07
got same problem but i solved it 
dcopserver was down so i tried to run it

 dcopserver

then look if you are owner of .kde directory in your home dir
if not try something like that being in your home

 sudo chown -R username .kde 

it worked in my system but i don't know if it is exactly the same problem
the errors in devices persist but k3b seems to work

bye

---

