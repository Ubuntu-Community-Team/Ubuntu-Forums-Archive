---
title: "Dual Boot Questions"
date: 2006-10-02
forum: Desktop Environments
---

### Post by lemonsCC on 2006-10-02
I currently have Xubuntu 6.06 installed on my "beige box of goodness" with its massive 30gb HD.  I want/NEED to install some form of windows on this box also (95, 98SE, 2000.)  I may be able to get 2000 Pro (no activation?) to install on this and need them to be able to dual boot.

My reason for doing this is simple, I need to be able to use ActiveSync to install medical references on my Dell Axim. 

[LIST]
[*]Is it possible to partition my HD for this install AND retain Xubuntu and all the files on it?
[*]How big should said partition be?  
[*]How big should said partition be?  
[*]Would the install (Win 2000) be the same as normal (pop the disk in and install on the new partition)?  
[*]How will grub know about the new boot choice? 
[/LIST]

---

### Post by adwait on 2006-10-02
It would be advisable to first install Windows and then install Linux and you will find that everything works as it should.

---

### Post by lemonsCC on 2006-10-02
Ok then is there a way to clone my current settings, setup, apps, users, file, etc and just dump them on there?

I am trying to minimize the downtime and the amount of work i need to do get this box running.

---

### Post by jys_sachin on 2006-10-02
I agree with adwait, since you have already installed ubuntu, it would be difficult for you to alter the boot options since GRUB is now installed on the MBR. Install windows 2000 first and then reinstall ubuntu and let GRUB do the rest...this also gives you an opportunity to re-configure your partitions while installing Ubuntu...8)

---

### Post by lemonsCC on 2006-10-02
Is there no way to reinstall Grub? If not what would be the procedure for installing the two OS?

---

### Post by adwait on 2006-10-03
There is a way to reinstall GRUB, but the problem is that windows needs to be on the first partition of a disk hence the problem.

---

