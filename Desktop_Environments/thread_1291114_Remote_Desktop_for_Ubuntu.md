---
title: "Remote Desktop for Ubuntu?"
date: 2009-10-14
forum: Desktop Environments
---

### Post by ccieadvisor on 2009-10-14
Hello-
I am new to Ubuntu and I really like it.  I could not beleive that once I installed it, it had ALL the Drivers that I needed for my new Desktop AND my OLD laptop. Regardless I have an issue I would like your help with please.
I need to "remote Desktop" from my New Windows 7 Laptop to my new Ubuntu Desktop.  What software can I use to do this and what software gets installed on which device?  Do I need something for just the windows box or just the Ubuntu or both etc..?? Thanks!!!

---

### Post by kanikilu on 2009-10-14
VNC is built-in, but I prefer FreeNX. You can get the NX Client for Windows from NoMachine. Here are some guides and a link to the Windows client:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

---

### Post by Rich_B_uk on 2009-10-14
Unless you have special requirements or bandwidth issues VNC will meet your needs. 

VNC comes in two parts - server and viewer. The 'server' gets installed on whatever machine you want to view, and the 'viewer' is installed on the machine you want to view from.

In Ubuntu, VNC support is automatically built in. To check it is enabled and configured to your liking go to **System > Preferences > Remote Desktop.**

Once you have the server side enabled and set up the way you like it you will need to install a viewer on your Windows PC. Note that the Remote Desktop app built into Windows is not compatible because it communicates using an entirely different closed protocol. The viewer I use is "UltraVNC" and you will easily track down the viewer using google.

Once it's all set up and the machines are on the same network you should be able to connect to the Ubuntu machine by specifying its IP or hostname.

---

### Post by ccieadvisor on 2009-10-14
> **kanikilu said:**
> VNC is built-in, but I prefer FreeNX. You can get the NX Client for Windows from NoMachine. Here are some guides and a link to the Windows client:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)

Big Thanks and so fast too.  I will try this and get back with everybody.

---

### Post by ccieadvisor on 2009-10-14
Wow, really thorough answers you guys are great.  I am going to install the Viewer on my Windows 7 and try to use vnc First since its already installed.  If I am not happy I will try the NX.  
I will return with the verdict so as to give back to the community.

---

### Post by kanikilu on 2009-10-14
VNC should work fine on a single user system. For a multi-user setup, NX (FreeNX) is the only viable solution that I've personally come across that allows clients on all major platforms (Windows, Mac, Linux) to securely connect to a Linux host.

---

### Post by Lars Noodén on 2009-10-14
krfb and krdc work well and are also part of ubuntu.  So you could show your KDE or Xfce desktop even to remote Windows users.

---

