---
title: "update manager doesn't show progress window, it's as if the UI doesn't update"
date: 2020-12-20
forum: Desktop Environments
---

### Post by Fallen Guru on 2020-12-20
This one is so weird I've no idea how to describe it, let alone what to search for ...
It happens on both of my 20.04 systems, an antique netbook and a Surface Go 2, both using Wayland session on Intel iGPU.

Say I start the update manager, or it pops up on its own, doesn't matter, anyway it displays a list of updates. I click the button telling it to go ahead, enter my password if needed.

I'd expect it to switch to the small window that displays status text and a progress bar.
Instead, no change. The window with the list of updates stays on screen, making me wonder whether I somehow managed to miss the button. Clicking it again does nothing, the UI elements don't react any more.

Now, the icon in the dock does show a progress bar, and checking ps the update seems to progress normally, it's just a visual bug. The kicker is that switching to a different workspace and back restores order: The lingering updates list window is gone and the small progress one is there.

The update manager isn't the only application that does this, windows lingering that should have been replaced by new ones happens elsewhere, too, it's just the most accessible example. 

I'd report a bug if I'd any idea against what ...

---

### Post by ActionParsnip on 2020-12-21
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

### Post by Fallen Guru on 2020-12-21
```

$ lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	20.04
Codename:	focal
Linux trapperkeeper 5.4.0-58-lowlatency #64-Ubuntu SMP PREEMPT Wed Dec 9 09:48:08 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

EDIT: That's the Surface Go 2

---

### Post by publicalpha on 2021-01-01
With same problem here since a month or so …
```
lsb_release -a; uname -a
LSB Version:    core-11.1.0ubuntu2-noarch:printing-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal
Linux buds-tp 5.4.0-59-generic #65-Ubuntu SMP Thu Dec 10 12:01:51 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by ajgreeny on 2021-01-01
Is the problem the same if you login using xorg instead of wayland?

---

### Post by publicalpha on 2021-01-22
Thank you for quick reply. Especially the problem is my update manager **doesn't show any progress bar.** Wenn i run the Update manager, first window shows up, load the sources, tell if there has to be update. Yes &#8212; now the following window appears blank only and doesnt work.

Is my Xubuntu running Xorg &#8212; may be so:
```
xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    12009000
X.Org version: 1.20.9
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
...

```

---

### Post by publicalpha on 2021-01-24
Wow, last update of Updater Core Module some days ago and it is fixed!

---

### Post by ActionParsnip on 2021-01-24
If there is no more issue then please mark as solved

---

