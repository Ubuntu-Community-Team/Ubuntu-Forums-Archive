---
title: "Garbled Login Screen"
date: 2007-07-19
forum: Desktop Environments
---

### Post by Jonq on 2007-07-19
Hi,

After trying to install my gfx cards driver Ati mobility x700, my login screen got garbled. its like 2 login sessions are on top of each other one working and one garbled after switching to tty and back to X makes them separate and i get non garbled version of the login while the garbled one running either F8 or F9.

is it normal to have two separate sessions running :confused: because I have checked gdm.conf and its has only 0=standard under its servers option.

i have searched forums and came across with this thread [http://ubuntuforums.org/showthread.php?t=149973](http://ubuntuforums.org/showthread.php?t=149973) I have added suggested option to my xorg.conf but still no change.

Anyone else have any other suggestions ? 

*[SIZE="1"]PS. gfx drivers working as expected and glxgears reports 3800fps[/SIZE]*

TIA

---

### Post by Death_Sargent on 2007-07-22
perhaps you are using a different kernel header. 

Try presing escape hen you get to the grub menu

chose the kernel with the highest version number. the name should end in "generic".

try it then see if it works.

---

