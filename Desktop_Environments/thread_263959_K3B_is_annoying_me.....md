---
title: "K3B is annoying me...."
date: 2006-09-24
forum: Desktop Environments
---

### Post by krazed nun on 2006-09-24
Ok, so i am using K3B to burn music. I like using my external drive better than the one that comes with the computer because it is way faster. BUt when i wanted to burn a CD on my external one, it said that cdrecord doesnt have permission to open my external drive. I searched the forums, but i cant find an answer. Another problem....I cant open the K3B setup. Its pretty wierd..
thanx in advance.:D

---

### Post by henriquemaia on 2006-09-24
> **krazed nun said:**
> [..] Another problem....I cant open the K3B setup. Its pretty wierd..
thanx in advance.:D

I'm not using k3b anymore, but as far as I remember, to open k3b setup, you had to run it as root. As such, if you type:

```
sudo k3bsetup
```

maybe you can open it. 

ps: check the command to k3b setup. I believe it that one, but not sure.

---

### Post by krazed nun on 2006-09-24
Tried it:

```
kingluis@BLEEK:~$ sudo k3bsetup
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
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
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
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kcmshell (kdelibs): WARNING: Could not find module 'k3bsetup2'.

```

:shock:

---

### Post by got_nix on 2006-09-24
Thats so odd. sudo or su k3b always works for me.. try kdesu k3b for the fun of it. hope it works for you..

---

