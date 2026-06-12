---
title: "problems with remote (on xming) display"
date: 2009-07-12
forum: Desktop Environments
---

### Post by esj on 2009-07-12
I'm trying to display Ubuntu/X11 applications via X11 (Xming) on a Windows virtual machine. The application will display just fine under Xming except for all the fonts being significantly smaller. Text displays are usually shown in nine point font and menu items/taskbar are similarly small.

I looked into this and I thought I needed some form of access to either fonts or a font server on the Xming server side but apparently, modern X11 environments let the clients manage all fonts and hinting. The server does nothing. If that's the case, why do I have such a tiny font displayed?

My test setup is:

Ubuntu 8.10 host
XP guest
Xming server
Putty for ssh tunneling
vmware workstation 6.5.2

At this point, somebody usually mentions VNC. I don't use it because it burns up way too many cycles, responsiveness is poor, degrades speech recognition accuracy, and, think about it for a moment. If the host os is running a vnc server and the guest is running Vnc client, what am I going to see?  Yup, the infinite hall of Windows.

I moved to Linux because it had the applications I needed. It was where my work ended up. It just didn't have speech recognition so I tried to run with a variety of virtual machines but either because of Windows stability problems or cross boundary problems like this, I am about ready to give up and be an all Windows shop just because I can't accommodate my disability in a Linux environment.

If I can solve this display problem then I can leave all my applications on Linux and display everything on Windows. I won't be happy but, it won't suck that much either.

thanks in advance.

---

