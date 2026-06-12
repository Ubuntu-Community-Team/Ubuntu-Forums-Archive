---
title: "Braid doesn't exist after installation"
date: 2011-08-04
forum: Gaming &amp; Leisure
---

### Post by SoylentSteak on 2011-08-04
I bought it from the Software Center, and after I install it and click on the launcher, nothing happens. I type "braid" in a terminal, and it says "command not found".

I checked the .braid folder, and it's** completely empty**. I've reinstalled several times, and it's still the same.

---

### Post by R33D3M33R on 2011-08-04
What does the search for the executable return?

```
find / -name braid
```

---

### Post by SoylentSteak on 2011-08-04
> **R33D3M33R said:**
> What does the search for the executable return?

```
find / -name braid
```

I got "permission denied", so I ran with it with sudo. It then accepted the command, but the result was absolutely nothing. Just a blinking cursor.

---

### Post by SoylentSteak on 2011-08-04
Wait, i just ckeck at the long list of "permission denied" and found

:

```
/usr/share/doc/braid
/usr/share/lintian/overrides/braid
/opt/braid
/opt/braid/braid

```

---

### Post by SoylentSteak on 2011-08-04
So I've found the executable using your help, but it does nothing when I clicky. I checked to make sure that the executing file is allowed as a program, and it is. 

What's the terminal command for this thing? If it's supposed to be "Braid" or "braid", it ain't working.

---

### Post by SoylentSteak on 2011-08-04
I ran nautilus with sudo to see what the terminal output would be when I clicked on the executable:

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x179
  Serial number of failed request:  125
  Current serial number in output stream:  127
```

---

### Post by SoylentSteak on 2011-08-04
Fixed!

```
sudo /opt/braid/braid -windowed
```

---

### Post by Perfect Storm on 2011-08-05
> **SoylentSteak said:**
> Fixed!

```
sudo /opt/braid/braid -windowed
```


Just don't run the game with sudo command. Sounds more like the permission of the game is set incorrectly.

---

### Post by SoylentSteak on 2011-08-05
> **Artificial Intelligence said:**
> Just don't run the game with sudo command. Sounds more like the permission of the game is set incorrectly.

Yes, in my piddling around to get it running I was throwing stuff against the wall to see what stuck. As it turns out, I can run it fine without sudo. Doing nautilus with sudo was the only way I could figure out how to get the error message to show in a terminal, and I didn't realize I no longer needed it.

I'm very careful with the sudo command; I only felt comfortable experimenting with it here because the worst thing I could screw up was a game that could be reinstalled anyway.

---

### Post by R33D3M33R on 2011-08-05
It appears that the braid executable wasn't linked to bin/sbin folder. That's why you couldn't launch it by typing braid. You should report this problem to the maintainers - file a bug in Launchpad.

---

