---
title: "USB stick auto-mounts for wrong user"
date: 2015-01-17
forum: Desktop Environments
---

### Post by inhumangeek on 2015-01-17
I am having trouble mounting USB sticks when two people are logged in at the same time. 

Let's say we have Paul and Emma, both are logged in but Paul is actually using the computer. It seems to auto-mount the USB stick in /media/emma/xxx rather than /media/paul. I have not tried it the other way around. Obviously there are workarounds such as logging Emma off, or mounting manually, or accessing /media/emma from Paul's account, but I would like to fix it properly. Any ideas?

Many thanks.

I am using Ubuntu 14.10.

---

### Post by sudodus on 2015-01-18
I see the problem, but I think the auto-mount cannot know which of the logged in users that plugged in the pendrive. I would recommend mounting manually, maybe using a shell-script or alias to make it more convenient.

Do you know how to make a shell-script or alias?

---

### Post by inhumangeek on 2015-01-18
Hi, thanks for the reply.

I know how to do both but unsure how to grab the UUID so I will look that up and maybe stick it in a script. I might just stick to the workarounds though as the user Emma would prefer to use automount I would think (and I don't use USB sticks that often).

Thanks again,
Paul

---

### Post by inhumangeek on 2015-01-18
Actually what I could do is write a script to unmount from Emma and re-mount as me - best of both worlds perhaps.

---

### Post by sudodus on 2015-01-18
That sounds like a good idea.

You can use ***df*** to identify the mounted pendrive's device and partition ID and ***sudo blkid*** to find the corresponding UUID (if you really need it). Or would you rather get the UUID before (once and for all) and point to it? Both ways are possible.

---

### Post by yancek on 2015-01-18
My experience with Ubuntu 14.04 given your parameters of users paul and emma.
Boot and login as emma and insert a flash drive and user emma will have access to do whatever on the flash drive.  Logout from user emma and login as user paul.  The flash is still mounted under /media/emma and not available for user paul.  If you try to access it when logged in as paul, you need to go to /media/emma and you will get access denied.  If user paul has root/sudo privileges he can open nautilus with:  gksu nautilus and acces it but otherwise not.

You can with root privileges as paul, use:  sudo umount to unmount the flash under /media/emma and then again use:  sudo mount command to mount to the /media/paul directory or of course, write a script to do this with sudo privileges.  

In my experience, the flash drive is mounted under /media of whatever user is loggied on when the flash is plugged in.  You should also have the option when logged in as emma to safely remove/eject or eject parent drive of the flash.  Then when logged in as paul, remove the flash from the port and plug it in again and have access as user paul.  The reverse is also true.  Logged in as paul, insert the flash and use it.  Safeley remove/eject and then remove and plug the flash in again when logged in as user emma.  Then you don't need to run the umount and mount commands.

---

