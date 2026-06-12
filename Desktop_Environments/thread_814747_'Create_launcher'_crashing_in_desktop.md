---
title: "'Create launcher' crashing in desktop"
date: 2008-06-01
forum: Desktop Environments
---

### Post by ne0h on 2008-06-01
I recently upgraded my laptop from dapper to hardy 8.04 xubuntu through CD that downloaded from internet. After one week or so, I tried to create a launcher from "Desktop -> Right Click -> Create Launcher" but it crashes when I about to type anything in the first text box of create launcher window i.e. "Name". Its just exiting. I don't know what's happening. But strangely if I type anything in other text boxes like "Comment" or "Command" its remains there, but crashing when I type any single letter in "Name" textbox. It was working previously. Why this weird behaviour suddenly?

Also, one thing couple of days back after upgrade I created one desktop shortcut manually -
```
[Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network; 
```
After this behaviour started, the short cut lost its icon and when I tried to execute (right click -> Execute) its not executing and opening in edit mode in "MousePad" and I also tried to "Edit Launcher" the same, but its exiting!!

---

### Post by ne0h on 2008-06-13
This is the entry of /var/log/messages -

```
Jun 13 21:27:58 ne0h-lappy kernel: [  225.981799] exo-desktop-ite[6443]: segfault at 00000000 eip b789dc37 esp bfc0b924 error 4
```

Please someone help. I can not create launcher :sad::sad::-(

---

### Post by igorthinks on 2008-08-12
I'm having exactly the same problem, but it isn't much known..

---

