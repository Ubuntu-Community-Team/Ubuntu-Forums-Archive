---
title: "Hangs on the splash screen while booting."
date: 2011-09-15
forum: Desktop Environments
---

### Post by gvivekcbe on 2011-09-15
Hi,

M/c - Core i7, NVidia GT 555M

Iam a newbie in Ubuntu. I installed Ubuntu 11.04 32 bit installed. I had the Unity desktop. I didnt install the additional NVIDIA 3D driver that the Ubuntu had listed. 

After the installation, there were three stages.

**First Stage:** Just after installation, everything was fine. Unity Interface was up.
**Second Stage:** Now after i installed the NVIDIA linux 32 bit driver, it boots to a terminal. And i was not able to start gdm with the gdm start/stop commands. I deleted the xconf file and apt-get removed NVIDIA*.
**Third Stage:** After i removed the NVIDIA driver, it hangs on the splash screen with those five dots forever blinking. I have to switch to the tty1 terminal and start gdm manually. Then it starts on the Ubuntu classic I/F.

Now how do i go to the first stage without re-installing.

Whats the fix for this? I do not want to install the NVIDIA driver. How can i bring it to the first state that i was in after i installed Ubuntu, without reinstalling it?

Thank you.

---

### Post by Blasphemist on 2011-09-16
Did you install the closed source nvidia driver? The install would install the open source driver. Try following the first few troubleshooting posts of this thread. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

