---
title: "No Keyboard/Mouse (PS2) in Intrepid after Updates"
date: 2009-04-16
forum: General Help
---

### Post by dbsoundman on 2009-04-16
I just installed Intrepid on an old Dell Workstation I have, which I also added a second processor to (before the installation). Install went smoothly, everything worked fine, I installed all the updates and also installed ssh, samba, and ubuntu-restricted-extras via synaptic. I used the ssh to call up my other desktop computer where I had backed up the smb.conf, menu.lst, sshd_config, ssh_config, and fstab files, and updated or replaced the ones on the Workstation machine. I then rebooted the Workstation, and found that the keyboard and mouse no longer work. I can do CTRL-ALT-DELETE, as well as CTRL-ALT-F1 to get to a command line. The command line works fine, but of course no ssh because the network isn't connected in that mode. I tried doing sudo dpkg-reconfigure xserver-xorg, but no success. I didn't really change any of the xorg settings, though, just re-ran the setup. What should I do next?

Thanks,
Dan

---

### Post by dbsoundman on 2009-04-16
OK, so I'm pretty sure the problem lies in the fact that I copied my old grub menu.lst over to my new computer, which means it refers to all the wrong kernels/places/things. So I booted into the live CD, ssh'd to my desktop computer, which also runs 8.10, and tried copying over that grub menu. Now I at least get a grub menu (for a while there I just deleted menu.lst, that didn't work out well), but ubuntu still doesn't boot because obviously the locations still aren't right for the ubuntu kernels. Is there a way to get grub to write a new menu.lst, or should I just reinstall again?

-Dan

---

