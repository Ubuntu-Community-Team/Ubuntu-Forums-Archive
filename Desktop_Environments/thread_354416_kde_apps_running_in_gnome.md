---
title: "kde apps running in gnome"
date: 2007-02-05
forum: Desktop Environments
---

### Post by deadowl on 2007-02-05
I have fallen in love with a few KDE apps. However, when I use a KDE app, the mouse cursor changes. I'm finding this a bit confusing. Anybody know if there's a way I can just use my mouse cursor that I use for everything else while using Amarok or KVpnc? It seems to only change cursors on events like hovering, or trying to drag something. I hope this isn't a stupid question.

---

### Post by aysiu on 2007-02-06
Press Alt-F2 and type ```
kcontrol
``` Then find Mouse under the Peripherals section. You can change the mouse theme there. You can also get more mouse themes [here](http://www.kde-look.org/index.php?xcontentmode=36&PHPSESSID=d227d36607d3d32f06b29e257568a6ba).

Maybe you can find one that matches your Gnome theme well.

---

### Post by deadowl on 2007-02-06
Oh darn, I remapped alt+f2, but I'll assume you mean the pseudo terminal. 

Yea, the mouse theme was set to system default, then I switched it to human. That didn't do anything, but I turned off open something on single click and that got rid of the ugly pointy finger on most things (because they're not links.

Still, drag/drop and hovering over something (like a link in a web page), will move the mouse theme to the ugly one (only within KDE apps, not affecting anything to do with window managing).

Black pointer, black pointer, black can't drop that here, absurdly long pointy finger. Is there anything else that might be controlling mouse cursors for KDE apps or something that I might not have installed for apps to work properly? BTW

:~$ kcontrol
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

Then there's also this when I play sudo:
ERROR: Communication problem with kcontrol, it probably crashed.

---

### Post by deadowl on 2007-02-08
Hmm, that's interesting, the strange loading cursor comes up when hovering over amarok on the notification area.

---

