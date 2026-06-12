---
title: "complete mess - partitions"
date: 2006-06-18
forum: Desktop Environments
---

### Post by sopo_dan on 2006-06-18
this just happened to me:
i come home and find my desktop shadowed over (like when you do "sudo" and it asks for password) and completely frozen, mouse won't move, no keys work, ctrl+alt+del doesn't work.

so i do a h/w reset. only to find out grub isn't loading. i do a "fdisk /mbr" off a dos boot floppy to be able to boot win. from here everything seems fine and i can also read all my linux partitions with the according total commander plugin.

now i boot the live cd to try and sort out the mess. 
in gparted i see sda10 has become sda6 and sda6-9 went sda7-10 (don't ask why i have that many partitions :p). 
i thought "wtf? ah, hell, i just edit fstab and menu.lst accordingly, then do grub -> root (hd0,8 ) -> setup (hd0) and that's it"
so i start doing that.
mounting /boot --> ok
editing menu.lst --> ok
mounting /root --> ok
editing /etc/fstab --> ok
mounting /home --> failed - returned some errors about ATA-something (stupid me didn't write it down) but i thought once the system would start it would do a check disk and maybe will be ok
install grub --> ok

now restart. i get grub displayed ok, i can boot win through it, but when i try booting linux it displays the info from menu.lst (root, initrd, vmlinuz) and then stops with this error: "Error 18: Selected cylinder exceeds maximum supported by BIOS"

i checked & double checked that all my references to sda* and (hd0,*) are the right ones.
what else can i do?? ](*,) except reinstalling of course. i had just finished fine-tuning the system to my liking & i really don't want to do that again soon.
and what could have caused this? i had no "weird" daemons running, no apps were running except gaim, skype and xmms which wasn't even playing

PS: sorry for the long post, but i tried giving as much info on this as i could

---

### Post by tchock on 2006-06-18
I'm not quite sure exactly what you're saying, but did you install grub to the MBR, or to /boot?

I'm not sure if this is still an issue with modern BIOSes, but if you installed grub to /boot, you should check to see if your /boot partition is past the 1024 cylinder boundary. You should be able to use gparted or partition magic to check this.

---

### Post by sopo_dan on 2006-06-18
as i said in the original post, i did "setup (hd0)" so i installed to mbr

---

### Post by sopo_dan on 2006-06-19
i was just thinking: would a reinstall & then copy all the old stuff over work?

PS: i'm stuck to windows for a day now & i can't stand it anymore ](*,) :cry:

---

