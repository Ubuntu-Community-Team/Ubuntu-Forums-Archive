---
title: "Error when installing GTKpod"
date: 2006-01-29
forum: Desktop Environments
---

### Post by 10010 on 2006-01-29
Hello everyone.  I'm new to ubuntu and have encountered an error when trying to install GTKpod using the "Add Applications" tool.

The following message is displayed:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Thank you for helping!

---

### Post by wondering_jew on 2006-01-29
Well it wouldn't fix the possible underlying problms but what happens when you try to get gtkpod from synaptic or just 'sudo apt-get install gtkpod' from a terminal?

---

### Post by RAOF on 2006-01-30
[QUOTE=10010]Hello everyone.  I'm new to ubuntu and have encountered an error when trying to install GTKpod using the "Add Applications" tool.

The following message is displayed:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Thank you for helping![/QUOTE]
The problem is that you don't have your Ubuntu CD in the drive - you'll notice those errors mention "cdrom://".  To stop Synaptic looking for the CD, go to Options->Repositories in Synaptic, and remove the one with "cdrom" in it.

---

### Post by 10010 on 2006-01-30
It worked, thank you both.

Time to tackle wireless internet!  ;)

---

