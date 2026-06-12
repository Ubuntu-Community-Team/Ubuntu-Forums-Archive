---
title: "X Error, weird..."
date: 2006-06-08
forum: Desktop Environments
---

### Post by neuronq on 2006-06-08
I have the following problem: whenever I launch a program form the terminal, I get some strange error, although the program usually runs normally. like, for example:

```
neuronq@neuronq-desktop:~$ konqueror
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

konqueror (or any other prog) runs fine, but smth tells me the problem can be more serious. hope someone can tell me what is it and how to fix it.

---

### Post by scxtt on 2006-06-08
mouse / keyboard misconfiguration?

---

### Post by arizonagroovejet on 2006-06-08
Try this:

Look in /etc/X11/xorg.conf and you'll find three lines

```
       InputDevice     "stylus" "SendCoreEvents"
       InputDevice     "cursor" "SendCoreEvents"
       InputDevice     "eraser" "SendCoreEvents"

```

Change them to

```
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
```

then log out and restart the X server. Or just reboot.

---

