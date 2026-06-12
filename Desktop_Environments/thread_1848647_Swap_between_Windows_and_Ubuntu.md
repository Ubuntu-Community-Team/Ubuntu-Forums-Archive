---
title: "Swap between Windows and Ubuntu"
date: 2011-09-22
forum: Desktop Environments
---

### Post by pareshb on 2011-09-22
Folks,

Is there a way to install Windows 7 and Ubuntu on a machine and have them run side by side and you swap between them without rebooting?

---

### Post by Copper Bezel on 2011-09-22
You might look into [_VirtualBox_]("http://www.virtualbox.org/"). You can create a virtual Windows machine which will run as a fullscreen application within Ubuntu, then leave it on one of your workspaces and switch between that way. It's not seamless, and the virtual machine will have some limitations, but VirtualBox's "guest additions" package, installed inside the Windows environment of the virtual machine, helps to simplify some of the more basic issues.

If you install the non-open-source version of VirtualBox from the website, you'll have some extra features, but there's an open source version in Ubuntu's repositories as well.

---

### Post by raja.genupula on 2011-09-23
> **Copper Bezel said:**
> You might look into [_VirtualBox_]("http://www.virtualbox.org/"). You can create a virtual Windows machine which will run as a fullscreen application within Ubuntu, then leave it on one of your workspaces and switch between that way. It's not seamless, and the virtual machine will have some limitations, but VirtualBox's "guest additions" package, installed inside the Windows environment of the virtual machine, helps to simplify some of the more basic issues.

If you install the non-open-source version of VirtualBox from the website, you'll have some extra features, but there's an open source version in Ubuntu's repositories as well.
+1 

Here a guide to help you , about installing windows 7 in virtual Box . 
[http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/](http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/)

All the best

---

### Post by YesWeCan on 2011-09-23
VirtualBox will also run in Windows so you can have Windows as your host OS and Ubuntu as a guest. The guest OS will run slower, especially for graphics-intensive apps, and will have graphics limitations and may have USB limitations. Running two OS's at the same time requires twice the RAM so you would be wise to have 2GB or more. So if you are a Windows gamer, for example, then run Windows as the VBox host and Ubuntu as guest.

---

### Post by ottosykora on 2011-09-23
You could use also PUBUNTU, this is ubuntu run on colinux.

[http://www.pendrivelinux.com/colinux-portable-ubuntu-for-windows/](http://www.pendrivelinux.com/colinux-portable-ubuntu-for-windows/)

With that, you have ubuntu panels on the winodws desktop, both work at the same time, similar like people have w7 on a mac.

But: need computer with quite some power, as the resources are shared in this case.

I played with it some time ago, don't know the current state if the project supports latest ubuntu versions.

---

### Post by 666f6f on 2011-11-13
> **ottosykora said:**
> You could use also PUBUNTU, this is ubuntu run on colinux.

+1 for coLinux, great technology. I have installed Debian as a Windows service and Samba in that Debian to share files with the Windows host.

---

### Post by TeamRocket1233c on 2011-11-13
Option 1: Partition the main hard drive in half, and install Ubuntu on the unused half, and set up NTLDR to acknowledge the existence of the other OS and try dual-booting that way.

Option 2: Install Ubuntu on a seperate hard drive, and set the bootloader up to recognize the second hard drive.

Option 3: Install Ubuntu on a virtual machine.

---

