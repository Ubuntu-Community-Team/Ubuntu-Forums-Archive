---
title: "Downgrading Dell"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by frbe0101 on 2007-10-23
As I have already posted here: [http://ubuntuforums.org/showthread.php?t=588033](http://ubuntuforums.org/showthread.php?t=588033)
My inspiron with 7.10 does not work (GUI down, X server down, etc) 
but I heard of a dell utility that will regress everything back to the factory installation, how do I do that (from a command prompt)?

---

### Post by Linicks on 2007-10-23
This only is available on pre-install Dell Ubuntu machines:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation)

Nick

---

### Post by notwen on 2007-10-23
I have responded in your previous post(please try to not make duplicate posts) and depending on your upgrade method, whether you installed from a Gutsy CD(possibly wiping your HDD's partitions) or upgrading through Update Manager you may/may not have lost your Dell Recovery partitions.  If you still have them, then you have nothing to worry about, reverting back to Dell's Feisty image will not be too difficult.  Simply hitting ESC during GRUB will bring up a OS select screen, from here select the very bottom option **"Reinstall Operating System"**.

Dell may also be releasing a new Gutsy image just as they released their own image of Feisty.  More info can be found [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").

---

