---
title: "Turn off guest OS in Virtualbox"
date: 2011-03-08
forum: Desktop Environments
---

### Post by tanyeun on 2011-03-08
in my opinion, it's wrong to turn off the operating system
by pushing the power off button on the hardware directly

but is it okay to do that in the Virtual Machine

I am running Windows XP on VirtualBox
sometimes I feels lazy to wait for windows to shut down
so I just close the window that runs the guest OS

will that do any harm to the host system? or the guest system
itself?

If I saved all the files that is important, I couldn't 
think of any side effect. Any ideas?

thx,

David

---

### Post by quattroman on 2011-03-08
Host wont suffer.

Guest OS will eventually suffer the same fate as turning off a real machine, OS files corrupted, boot to safe mode menu, check disk, failing profiles. 

In that case, if feeling lazy, do the save state option when closing the virtual Box. Takes couple of seconds, and will load into the last known state next time. Also the state is saved if you shutdown host machine.

---

### Post by doas777 on 2011-03-08
ok, the danger to shutting down ungracefully deals primarily with your hard disks. you run into problems if the disk had data that still needed written in the disk cache, or if it was in the process of writting data at the time of the power off. if neither of these is true then you dont ahve a problem, but if they are, you run a good risk of corrupting the filesystem of your virtual hard disk. 

when possible shutdown from within the guest, or send a shutdown signal to the guest. failing all else, saving the machine state will allow you to pause the guest for a host reboot or whatever.

---

### Post by tanyeun on 2011-03-09
thx for the reply guys :D

---

