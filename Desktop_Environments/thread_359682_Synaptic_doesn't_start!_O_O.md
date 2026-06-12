---
title: "Synaptic doesn't start! O_O"
date: 2007-02-12
forum: Desktop Environments
---

### Post by MasterOfMuppets on 2007-02-12
In KDE Edgy here, and I can't start the synaptic package manager... It shows the task in the taskbar but then it vanishes and nothing happens. Any Ideas?

---

### Post by an.echte.trilingue on 2007-02-12
Are you trying to launch it with gktsu synaptic or kdesu synaptic?  Does adept work?

---

### Post by MasterOfMuppets on 2007-02-12
Adept works, although like the newb I am i never ever used it...
I'm trying to launch it via Kmenu.

---

### Post by an.echte.trilingue on 2007-02-12
I can understand a preference for synaptic over adept.  So what happens when you type these two things into a terminal:

```
gksu synaptic
kdesu synaptic
```

---

### Post by MasterOfMuppets on 2007-02-12
gksu synaptic works just fine. Is that a GNOME comm?
kdesu gives me this:

[COLOR="Navy"]X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
[/COLOR]

but works fine.

---

### Post by an.echte.trilingue on 2007-02-12
gksu is the the gnome su frontend, kdesu is the one for kde, but it does not really make much difference which you use (I sometimes have issues with kdesu crashing, though).  Since they both work, you can just right click on the kmenu, and edit the menu.  Go to the synaptic entry, and where it says "command", you can simply replace that with "gksu synaptic" or "kdesu synaptic", whichever you think looks better.

Take care
-mat

---

