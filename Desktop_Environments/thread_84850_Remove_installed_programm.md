---
title: "Remove installed programm?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by xsence on 2005-11-01
Hi is there a list with installed programms? not in synaptics. .i have installed doom3 and enemy territory but can't find a way to remove them.

---

### Post by GrumpyBob on 2005-11-01
If you installed these via apt or synaptic, they should show up in synaptic and you can select uninstall.

How did you install them?

Robert

---

### Post by xsence on 2005-11-01
it where .run files so i did "sudo sh blabla.run"

---

### Post by RAOF on 2005-11-01
Things that you install in that way don't have any unified way to uninstall.  They may be able to uninstall themselves, if the makers have been good.  You might be able to sudo <whatever>.run --uninstall.  Many of them should respond to ./<whatever>.run --help, giving a list of command-line options (including, hopefully, uninstalling).

But the bottom line is that anything you install outside of apt/synaptic is going to be different, and may not even have the facility to uninstall itself.

---

