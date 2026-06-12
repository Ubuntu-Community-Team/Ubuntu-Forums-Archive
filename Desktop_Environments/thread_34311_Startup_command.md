---
title: "Startup command?"
date: 2005-05-14
forum: Desktop Environments
---

### Post by SmokingGun on 2005-05-14
Can anyone tell me how i can run a startup command when i boot?  Such as....

hdparm -B 244 /dev/hda

rather than having to enter it manually each time?

---

### Post by nad on 2005-05-14
Computer->Desktop Preferences->Sessions will allow you to add a startup script to your session login.

Other than that, system startup scripts are located in /etc/init.d with links in the appropriate runlevel directories, rcS.d, rc1.d, rc2.d, etc.

You could also edit gdm's resources files, but you might break something here.

---

### Post by Alexander Kirillov on 2005-05-14
[QUOTE=nad]Computer->Desktop Preferences->Sessions will allow you to add a startup script to your session login.[/QUOTE]

These commands will be executed when you login to GNOME, not at boot time. 

To execute command at boot time, you need to edit initlevel rcS

However, for hdparm,  there is a special config file  -IIRC, /etc/hdparm (I am away form my Ububnut box, so can't check - search the forums for hdparm or dma), where you can just set hdparm parameters for  all disks.

---

### Post by nad on 2005-05-14
The boot script is /etc/hdparm.conf . This may be edited.

As GNU/Linux is all about choice, there is usually more than one way to do configuration often depending on your specific requirements.

---

