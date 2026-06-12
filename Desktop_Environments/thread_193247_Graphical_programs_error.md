---
title: "Graphical programs error"
date: 2006-06-09
forum: Desktop Environments
---

### Post by elbryan on 2006-06-09
Hi!
It's quite simple to explain my issue ..

When, in console, i write "kate, kwrite" or similar applications that use the XServer i give this
```

elbryan@ubuntu:~$ kate
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
ScimInputContextPlugin()

```

The application shows without any problem but it's quite annoying seeing this everytime..
Is it just a bug to ignore or a problem?

---

### Post by zxee on 2006-06-10
I was going to suggest doing xhost + localhost to see if that would clear up the errors. (I don't get those in ubuntu/gnome) there are however threads about this here for kubuntu. here's one; [http://www.ubuntuforums.org/showthread.php?t=185930](http://www.ubuntuforums.org/showthread.php?t=185930)
but there are several others. Hope that helps.

---

