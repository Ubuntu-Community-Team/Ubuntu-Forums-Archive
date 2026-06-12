---
title: "How to open firefox from tty terminal?"
date: 2011-05-21
forum: Desktop Environments
---

### Post by scott_tiger on 2011-05-21
After pressing  ctrl+shift+F1 I go to the tty1 cmd line terminal.

But I am not able to open firefox or chromium browser by typing their name in cmd line terminal.How to open the browser from cmd line.?

Also in /media directory I am not able to automatically mount my C: D: E: drives. I need to click Places and then drive name to mount the drives.My C: D: E: are windows drives and need to automatically mount in ubuntu after starting?

Any help...

---

### Post by sanderj on 2011-05-21
> **scott_tiger said:**
> After pressing  ctrl+shift+F1 I go to the tty1 cmd line terminal.

But I am not able to open firefox or chromium browser by typing their name in cmd line terminal.How to open the browser from cmd line.?



CTRL + SHIFT + F1? And that works? Which Ubuntu version are you using? I would say a very old one.

Anyway: you should not type CTRL + SHIFT + F1. You should type ALT + F2, and then 'xterm' or 'gnome-terminal', and in that terminal 'firefox' and then ENTRE.

HTH

---

### Post by Plueonic on 2011-05-21
> **scott_tiger said:**
> After pressing  ctrl+shift+F1 I go to the tty1 cmd line terminal.
But I am not able to open firefox or chromium browser by typing their  name in cmd line terminal.How to open the browser from cmd line.?

```
DISPLAY=:0 firefox
```It would still be displayed on the X server that is currently running, if there is any (ctrl+alt+F7)
> **scott_tiger said:**
> 
Also in /media directory I am not able to automatically mount my C: D:  E: drives. I need to click Places and then drive name to mount the  drives.My C: D: E: are windows drives and need to automatically mount in  ubuntu after starting?You could use pysdm or any other GUI tool to do that but learning to edit [COLOR=Red][/etc/fstab]("https://help.ubuntu.com/community/Fstab")[/COLOR] manually has its advantages =)
Post back the output of *sudo blkid -c /dev/null* if need further help

---

