---
title: "Visual effects changing on reboot"
date: 2010-02-13
forum: Desktop Environments
---

### Post by donaldkm on 2010-02-13
Hi,
    I am running Ubuntu 9.1 and I started having a problem with the Visual Effects defaulting to NONE instead of CUSTOM after I reboot. I can select CUSTOM and everything appears fine, however after I restart it returns to NONE. Is there anyway that my preferred  setting can be selected and remain selected until I choose to change it. Thank You.

---

### Post by howefield on 2010-02-13
Try loading up gconf-editor and navigate to desktop > gnome > applications > window_manager and change the default to compiz.

To open gconf-editor, open a run box by pressing alt + F2 keys together and type gconf-editor.

---

### Post by ajgreeny on 2010-02-13
I don't think howefield's answer will get you anywhere as those keys are no longer active.  Try adding compiz to the Startup Applications in System->Preferences.

---

### Post by donaldkm on 2010-02-13
I tried the  gconf-editor and compiz was already the default. I also tried to add compiz to start up applications, with the same same results. I can't seem to nail down what is changing my selection.

---

### Post by JohnFante on 2010-02-18
Same problem here. Compiz resets back to no effects after reboot. Both when I use fusion-icon and normal desktop effects.

---

### Post by JohnFante on 2010-02-18
Found a solution:

[http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2](http://ubuntuforums.org/showthread.php?t=1000965&highlight=compiz+resets&page=2)

Hope this helps you also!

---

