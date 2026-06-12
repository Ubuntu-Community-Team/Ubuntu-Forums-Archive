---
title: "Grab handles look odd on some windows"
date: 2011-05-19
forum: Desktop Environments
---

### Post by lifelike27 on 2011-05-19
Does anyone else have this problem? [http://ubuntuone.com/p/uRp/](http://ubuntuone.com/p/uRp/)

It's fine for the terminal and nautilus: [http://ubuntuone.com/p/uRq/](http://ubuntuone.com/p/uRq/)

There are ways of 'hiding' it as shown [_here_]("http://www.omgubuntu.co.uk/2011/05/disable-the-resize-grip-in-ubuntu-11-04/"), but I wanted to fix this bug rather than hide it.

---

### Post by lifelike27 on 2011-05-22
Is no one replying because it's a stupid question (i.e it's mentioned somewhere else I haven't looked that this is a known, unsolvable issue) or just bad luck?

---

### Post by Larkspur on 2011-05-22
Well, the solution you linked to seems to be the best way to resolve it.  According to the [thread]("http://askubuntu.com/questions/29209/disable-resize-gripper-in-windows") omgubuntu seem to have got the fix from, applying that for all themes (without editing the .gtkrc files) could involve recompiling gtk itself.

---

### Post by lifelike27 on 2011-05-22
So I added that code to the file and it's taken off the grab handles for all other windows except chrome, which was the original reason I wanted to remove them...

---

### Post by Larkspur on 2011-05-22
> **lifelike27 said:**
> So I added that code to the file and it's taken off the grab handles for all other windows except chrome, which was the original reason I wanted to remove them...

Have you got Chrome using its default theme or have you chosen the option for gtk intergration (or whatever it is - it's been a while since I've used Chrome)?

---

### Post by lifelike27 on 2011-05-22
Yup, it also appears with the Chrome 'classic' theme as well, except it's blue then.

---

### Post by Larkspur on 2011-05-22
Have you logged out at any time?  Sometimes, that's all it takes for a new theme to be fully applied.  It's not likely in this case, sadly; [Chromium]("http://code.google.com/p/chromium/issues/detail?id=75048") and [a whole load of other apps]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/704105") are affected, and it seems no one has come up with a fix yet.

---

### Post by lifelike27 on 2011-05-24
Shame. It looks odd. =\

---

### Post by lifelike27 on 2011-06-05
This problem is solved in Chrome Unstable (v13).

Will just have to wait for the stable release then.

---

