---
title: "This mornings update (July 11th 2006) broke my system"
date: 2006-07-11
forum: Desktop Environments
---

### Post by sefs on 2006-07-11
They were a whole bunch of em

but what springs too mind are the new kernel and a new nvidia-glx-legacy


After updating system seemed to reboot fine.  then it got slow, then apps would not open and lost network connectivity.

Rebooted GDM would not start unplugged net work card ... boots up.

Plugged back in network usb card system cannot start apps or starts them way too slowly.

Unplugged network card .. system can again start apps but system seems to be unstable.

I had to recompile the ndiswrapper ver 1.16 for the new kernel.

Is anyone else experiencing any system instability with these new set of updates.

Thanks.

---

### Post by dasyar613 on 2006-07-11
I am running amd64, this mornings update consisted of cupsys and the amd64. Everything seems to working just fine. The only mishap was the cupsys, it did not install, or at least it said it ignored a lot of files when trying to update. The weird thing is, when I went to the update manager, it shows that everything was up to date. So, who knows, but overall everything is working just fine.

---

### Post by MonkeyNet on 2006-07-11
Part of this might have to do with the Nvidia drivers.

If you have custom compiled your own kernel, then you may need to reinstall the nvidia drivers.

Have a look at [this HOWTO]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") and see if it is relevant.

I am not sure where I saw it, but have seen written somewhere that kernel updates can have effects on the nvidia drivers depending on how they have been compiled on the system. 

This may not be the answer, but would be a good place to start looking. At this stage I am still running on the 2.6.15-25 so will let you know if I have any issues on the latest kernel.

cheers,

Andrew

---

### Post by sefs on 2006-07-11
The kernel is the one that came with the ubuntu distribution and the nvidia stuff from synatic. I dont think its a custom made one.  I am on the 32 bit system thing though, not the 64 bit.

---

### Post by sefs on 2006-07-11
Hi.

Somehow it was the /etc/hosts file that got trashed.  

Maybe it was the update maybe it was my modem? not too sure.

But I had to reboot my modem.  Aslo apps like user manager and synatic would not work.  Sudo command was giving a gethostbyname error.  All due to a corrupt host file.

I had previously updated it to one of those ad blocking host files and somehow today it got messed up.

So after restoring it to a proper format and rebooting the modem every thing went back to normal.

Thanks all.

---

### Post by cptnapalm on 2006-07-11
Not entirely relating to this thread, but I've had problems with the /etc/hosts file too.  I assumed it had something to do with Xgl and compiz lockups and the subsequent hard reboots mucking up my filesystem.

Might want to check your /etc/samba/smb.conf file... if that file is screwy too then something very odd is going on.

---

