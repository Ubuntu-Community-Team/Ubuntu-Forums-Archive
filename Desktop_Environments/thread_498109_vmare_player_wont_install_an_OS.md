---
title: "vmare player wont install an OS"
date: 2007-07-10
forum: Desktop Environments
---

### Post by eersan123 on 2007-07-10
Hi im running Xubuntu on a panasonic cf-w2 and trying to get vmare to install window 2k but it gives me an error . It said ntkrnlmp.exe couldn't be load.error code 7. I tried to install window 2k b4 i switch to xubuntu and it also  show the same message. plz help

---

### Post by katanacb on 2007-07-11
Hi there.  Just a few thoughts.

VMware player isn't designed to install guest OS's, you have to use VMware workstation for that.  I'm not sure if that's your problem or not, but there are some differences between the player product and the workstation product in that regard.

If you are using workstation to try and install the guest, are you getting the error as soon as you try installing Win2K, or are you getting this problem *after* doing the install and trying to reboot the VM for the first time?  Anything reporting an error in the VM's log file?  Also, I've seen some issues before with installing from CD's into guests ... go into the VM's configuration screen, then pull up the section that talks about CD-ROM drives, check the 'legacy emulation' checkbox and try again ... that's solved some problems for me before with trying to get things installed from CD.

---

### Post by eersan123 on 2007-07-11
i tried using vmware workstation and i still get the same error, i used another window 2k disc and i still get the same error

---

### Post by mbsullivan on 2007-07-11
Hi,

katanacb is right... VMWare Player is not made for creating disk images. VMware Server (which is now free [beer]) or Workstation is better if you actually have to install anything to the disk. That being said, so long as you already have the virtual disk created (done manually, or through another program?), VMWare Player SHOULD (I think) still be able to install to it. Sounds iffy, though. You might want to try one of the other VMWare products, or VirtualBox, or Qemu + KVM.

Mike

---

