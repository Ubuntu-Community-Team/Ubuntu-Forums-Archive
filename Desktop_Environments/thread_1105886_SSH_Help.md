---
title: "SSH Help"
date: 2009-03-25
forum: Desktop Environments
---

### Post by Diverted Income on 2009-03-25
Is there a good guide for a How To SSH for a newbie? Looking to SSH across a LAN first then want to connect from external network at some point. 
Thanks!

---

### Post by lovinglinux on 2009-03-25
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by Diverted Income on 2009-03-25
Thanks! I'm reading now. Looks like what I need to get started.

---

### Post by Diverted Income on 2009-03-28
Ok I can SSH to the machines. I am still having trouble pulling the desktop across or running applications. I get an error that no video specified. trying     firefox & for a command. What am I missing now? 
Thanks!

---

### Post by lovinglinux on 2009-03-28
> **Diverted Income said:**
> Ok I can SSH to the machines. I am still having trouble pulling the desktop across or running applications. I get an error that no video specified. trying     firefox & for a command. What am I missing now? 
Thanks!

I'm not sure you can pull the desktop. I guess only remote desktop can do this, not ssh. Anyways, to run applications you need to configure the ssh server on the remote machine to forward the X server. Then put the option -X in the ssh command.

---

### Post by Diverted Income on 2009-03-28
So can I use SSH to connect then establish a VNC or Remote Desktop securely?

---

### Post by Dr Small on 2009-03-28
> **lovinglinux said:**
> I'm not sure you can pull the desktop. I guess only remote desktop can do this, not ssh. Anyways, to run applications you need to configure the ssh server on the remote machine to forward the X server. Then put the option -X in the ssh command.
Sure SSH can pull the desktop. You just gotta use the -X flag, and Xephyr:
[http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

### Post by lovinglinux on 2009-03-28
> **Dr Small said:**
> Sure SSH can pull the desktop. You just gotta use the -X flag, and Xephyr:
[http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

Thanks. Everyday on this forum is a new learning experience ;)

---

### Post by Dr Small on 2009-03-28
> **lovinglinux said:**
> Thanks. Everyday on this forum is a new learning experience ;)
I know it! That's why I'm lovinglinux :)

---

