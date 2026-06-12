---
title: "How can I change and make a boot screen?"
date: 2013-04-19
forum: Desktop Environments
---

### Post by thisislinuxdj on 2013-04-19
:confused::confused::confused:I would like to know how I could change kubuntu boot screen that got there after I installed kde desktop. I would like to make my own boot because making my own ubuntu based distro and would like own boot screen. thanks for support! :KS:KS:):)  Think i aready figured out how to change background grub screen/ or splash screen I think.

---

### Post by oldfred on 2013-04-19
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

I do not know Kubuntu, but some ideas here?

  Magnificent March Screenshot Thread 
[http://ubuntuforums.org/showthread.php?t=2121094](http://ubuntuforums.org/showthread.php?t=2121094)
Amazing April Screenshots
[http://ubuntuforums.org/showthread.php?t=2131337](http://ubuntuforums.org/showthread.php?t=2131337)

---

### Post by thisislinuxdj on 2013-04-20
ok thanks. but boot was just changed to kubuntu boot in from ubuntu 12.04 boot when i installed kde desktop. so i don't think it would be different between two. know how to change splash grub screen but. don't know how to make a boot screen. and change it.

---

### Post by thisislinuxdj on 2013-04-20
:(

---

### Post by grahammechanical on 2013-04-20
In Ubuntu we get a purple splash screen. In Kubuntu we get a grey(?) screen. Is it this that you wish to alter? I think you need to search in the system folders for things relating to Plymouth.

This may help [break the loading process :) ]  go to /lib/plymouth/themes  and poke around in the details, ubuntu-logo, & ubuntu-text folders. Study the scripts. You will need administrator privileges to edit them but make sure you have a back up copy. If I was going to mess around with this I would be messing up ubuntu-logo.script.

Regards.

---

