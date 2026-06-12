---
title: "[SOLVED] kubuntu gutsy compiz fusion no window management"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by mpgarate on 2007-09-17
whenever I try to run compiz-fusion, everything works, animations, 3d cube, except window borders and management. neither kde-window-manager --replace nor emerald --replace work. The do nothing but return this:

> X Error: BadDevice, invalid or uninitialized input device 171
Major opcode: 149
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
Major opcode: 149
Minor opcode: 3
Resource id: 0x0
Failed to open device

---

### Post by Forlong on 2007-09-17
This output has nothing to do with Compiz but with the wacom entries of your xorg.conf that Ubuntu chose to put there by default.

To get your window boarders back, you can try the steps in the *Troubleshooting* section under "No window boarders (titlebars)" [here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").

---

### Post by mpgarate on 2007-09-17
thanks for the help.... and also I believe this is unrelated.. but im having some package trouble...

> The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins but it is not going to be installed
          Depends: compiz-gnome but it is not going to be installed
          Depends: compiz-fusion-plugins-main (>= 0.5.2+git20070917) but it is not going to be installed
          Depends: compiz-fusion-plugins-extra (>= 0.5.2+git20070917) but it is not going to be installed
          Depends: libcompizconfig0 (>= 0.5.2+git20070912-0ubuntu2) but 0.5.2+git20070912-0ubuntu1 is to be installed
E: Broken package

---

### Post by mpgarate on 2007-09-17
I'm trying

> sudo apt-get -f install compiz

and it seems to be working

---

### Post by mpgarate on 2007-09-17
solved! thank you very much!

---

