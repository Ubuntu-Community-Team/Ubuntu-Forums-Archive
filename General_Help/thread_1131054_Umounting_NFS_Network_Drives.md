---
title: "Umounting NFS Network Drives"
date: 2009-04-20
forum: General Help
---

### Post by kacike76 on 2009-04-20
Hi, 

I have a NAS with NFS configured which automatically mounts its shares on my HP Proliant Dv7-1025nr laptop running Ubuntu 8.10, 64 bit. I have configured my /etc/fstab file with 3 different mount points. It works fine on boot up and all the shares are mounted. The only problem now is going into suspend and hibernate and even shutting down the laptop (sometimes). The laptop refuses to go into suspend or hibernate unless the drives are unmounted. I tried writing a script in both directories: /etc/acpi/suspend.d and /etc/acpi/resume.d to automatically unmount the drives on suspend and mount on resume. 

The scripts look like this: 
#!/bin/sh

umount /media/nasmedia/NASMovies
umount /media/nasmedia/NASMedia
umount /media/nasmedia/NASFred_Doc

#!/bin/sh

mount /media/nasmedia/NASMovies
mount /media/nasmedia/NASMedia
mount /media/nasmedia/NASFred_Doc

I have permissions 777 on both scripts. Both scripts work fine when executed from terminal. After executing the umount script from terminal, the laptop suspends fine. The problem is, i don't want to have to run this scritp manually everytime before closing the lid and my girlfriend won't know how to do it. Is there a way to successfully write a script that will do this automatically. I suspect this is an issue related to permissions as mount and umount are root commands.

---

