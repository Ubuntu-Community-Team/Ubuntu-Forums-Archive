---
title: "x2go not working"
date: 2021-08-07
forum: Desktop Environments
---

### Post by sniper8752 on 2021-08-07
I have an ubuntu server running x2go, and a x2go client.  When I attempt to connect, it fails.  I am able to capture the output.  How do I resolve this so I can remotley access the machine's gui? 

```


NXPROXY - Version 3.5.99.23


Copyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)
Copyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>
Copyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>
Copyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>
Copyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>
Copyright (c) 2015-2016 Qindel Group (http://www.qindel.com)


NXCOMP, NX protocol compression and NX extensions to this software
are copyright of the aforementioned persons and companies.


Redistribution and use of the present software is allowed according
to terms specified in the file LICENSE.nxcomp which comes in the
source distribution.


All rights reserved.


NOTE: This software has received contributions from various other
contributors, only the core maintainers and supporters are listed as
copyright holders. Please contact us, if you feel you should be listed
as copyright holder, as well.


NX protocol compression is derived from DXPC project.


Copyright (c) 1995,1996 Brian Pane
Copyright (c) 1996,1997 Zachary Vonler and Brian Pane
Copyright (c) 1999 Kevin Vigor and Brian Pane
Copyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane


All rights reserved.


See https://github.com/ArcticaProject/nx-libs for more information.


Info: Proxy running in server mode with pid '18510'.
Session: Starting session at 'Fri Aug  6 18:05:39 2021'.
Info: Using errors file '/home/user/.x2go/S-user2-50-1628287536_stDGNOME_dp24/sessions'.
Info: Using stats file '/home/user/.x2go/S-50/stats'.
Loop: WARNING! Overriding auxiliary X11 port with new value '1'.
Warning: Overriding auxiliary X11 port with new value '1'.
Info: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.
Info: Connecting to remote host 'localhost:38113'.
Info: Connected to remote proxy on FD#5.
Info: Connection with remote proxy completed.
Loop: WARNING! Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Info: Using ADSL link parameters 1408/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_24'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding auxiliary X11 connections to display ':0'.
Session: Session started at 'Fri Aug  6 18:05:39 2021'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Fri Aug  6 18:05:47 2021'.
Session: Session terminated at 'Fri Aug  6 18:05:47 2021'.


NXPROXY - Version 3.5.99.23


Copyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)
Copyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>
Copyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>
Copyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>
Copyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>
Copyright (c) 2015-2016 Qindel Group (http://www.qindel.com)


NXCOMP, NX protocol compression and NX extensions to this software
are copyright of the aforementioned persons and companies.


Redistribution and use of the present software is allowed according
to terms specified in the file LICENSE.nxcomp which comes in the
source distribution.


All rights reserved.


NOTE: This software has received contributions from various other
contributors, only the core maintainers and supporters are listed as
copyright holders. Please contact us, if you feel you should be listed
as copyright holder, as well.


NX protocol compression is derived from DXPC project.


Copyright (c) 1995,1996 Brian Pane
Copyright (c) 1996,1997 Zachary Vonler and Brian Pane
Copyright (c) 1999 Kevin Vigor and Brian Pane
Copyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane


All rights reserved.


See https://github.com/ArcticaProject/nx-libs for more information.


Info: Proxy running in server mode with pid '18605'.
Session: Starting session at 'Fri Aug  6 18:07:32 2021'.
Info: Using errors file '/home/user/.x2go/S-user2-50-1628287649_stDGNOME_dp24/sessions'.
Info: Using stats file '/home/user/.x2go/S-50/stats'.
Loop: WARNING! Overriding auxiliary X11 port with new value '1'.
Warning: Overriding auxiliary X11 port with new value '1'.
Info: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.
Info: Connecting to remote host 'localhost:53567'.
Info: Connected to remote proxy on FD#5.
Info: Connection with remote proxy completed.
Loop: WARNING! Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Info: Using ADSL link parameters 1408/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_24'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding auxiliary X11 connections to display ':0'.
Session: Session started at 'Fri Aug  6 18:07:32 2021'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Fri Aug  6 18:07:36 2021'.
Session: Session terminated at 'Fri Aug  6 18:07:36 2021'.


NXPROXY - Version 3.5.99.23


Copyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)
Copyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>
Copyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>
Copyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>
Copyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>
Copyright (c) 2015-2016 Qindel Group (http://www.qindel.com)


NXCOMP, NX protocol compression and NX extensions to this software
are copyright of the aforementioned persons and companies.


Redistribution and use of the present software is allowed according
to terms specified in the file LICENSE.nxcomp which comes in the
source distribution.


All rights reserved.


NOTE: This software has received contributions from various other
contributors, only the core maintainers and supporters are listed as
copyright holders. Please contact us, if you feel you should be listed
as copyright holder, as well.


NX protocol compression is derived from DXPC project.


Copyright (c) 1995,1996 Brian Pane
Copyright (c) 1996,1997 Zachary Vonler and Brian Pane
Copyright (c) 1999 Kevin Vigor and Brian Pane
Copyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane


All rights reserved.


See https://github.com/ArcticaProject/nx-libs for more information.


Info: Proxy running in server mode with pid '54151'.
Session: Starting session at 'Sat Aug  7 15:13:39 2021'.
Info: Using errors file '/home/user/.x2go/S-user2-50-1628363616_stDGNOME_dp24/sessions'.
Info: Using stats file '/home/user/.x2go/S-50/stats'.
Loop: WARNING! Overriding auxiliary X11 port with new value '1'.
Warning: Overriding auxiliary X11 port with new value '1'.
Info: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.
Info: Connecting to remote host 'localhost:58585'.
Info: Connected to remote proxy on FD#5.
Info: Connection with remote proxy completed.
Loop: WARNING! Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Info: Using ADSL link parameters 1408/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_24'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding auxiliary X11 connections to display ':0'.
Session: Session started at 'Sat Aug  7 15:13:40 2021'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sat Aug  7 15:13:45 2021'.
Session: Session terminated at 'Sat Aug  7 15:13:45 2021'.


NXPROXY - Version 3.5.99.23


Copyright (c) 2001, 2011 NoMachine (http://www.nomachine.com)
Copyright (c) 2008-2014 Oleksandr Shneyder <o.shneyder@phoca-gmbh.de>
Copyright (c) 2014-2016 Ulrich Sibiller <uli42@gmx.de>
Copyright (c) 2014-2016 Mihai Moldovan <ionic@ionic.de>
Copyright (c) 2011-2016 Mike Gabriel <mike.gabriel@das-netzwerkteam.de>
Copyright (c) 2015-2016 Qindel Group (http://www.qindel.com)


NXCOMP, NX protocol compression and NX extensions to this software
are copyright of the aforementioned persons and companies.


Redistribution and use of the present software is allowed according
to terms specified in the file LICENSE.nxcomp which comes in the
source distribution.


All rights reserved.


NOTE: This software has received contributions from various other
contributors, only the core maintainers and supporters are listed as
copyright holders. Please contact us, if you feel you should be listed
as copyright holder, as well.


NX protocol compression is derived from DXPC project.


Copyright (c) 1995,1996 Brian Pane
Copyright (c) 1996,1997 Zachary Vonler and Brian Pane
Copyright (c) 1999 Kevin Vigor and Brian Pane
Copyright (c) 2000,2003 Gian Filippo Pinzari and Brian Pane


All rights reserved.


See https://github.com/ArcticaProject/nx-libs for more information.


Info: Proxy running in server mode with pid '54188'.
Session: Starting session at 'Sat Aug  7 15:13:57 2021'.
Info: Using errors file '/home/user/.x2go/S-user2-50-1628363634_stDGNOME_dp24/sessions'.
Info: Using stats file '/home/user/.x2go/S-50/stats'.
Loop: WARNING! Overriding auxiliary X11 port with new value '1'.
Warning: Overriding auxiliary X1Info: Connection with remote proxy completed.
Loop: WARNING! Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Info: Using ADSL link parameters 1408/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_24'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding auxiliary X11 connections to display ':0'.
Session: Session started at 'Sat Aug  7 15:13:58 2021'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
1 port with new value '1'.
Info: Using abstract X11 socket in kernel namespace for accessing DISPLAY=:0.
Info: Connecting to remote host 'localhost:33431'.
Info: Connected to remote proxy on FD#5.



```

---

### Post by scorp123 on 2021-08-07
What desktop environment / window manager is even installed on that server? You can't connect e.g. to KDE if KDE is not even installed...

---

### Post by TheFu on 2021-08-08
Does ssh work from the client to the server? That's a mandatory requirement FIRST.

---

### Post by sniper8752 on 2021-08-12
Yes, I can ssh.  And it's gnome.

---

### Post by TheFu on 2021-08-12
Gnome doesn't work remotely.  It demands direct access to the GPU. Pick almost any other DE, install it, then change the x2go-client connection settings to use the different DE.

---

### Post by ActionParsnip on 2021-08-13
I'd suggest LXDE but what are you wanting to do on the remote system? Why do you need the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by sniper8752 on 2021-08-13
I have virtualbox installed, and want to control my VMs.

---

### Post by QIII on 2021-08-13
Like any server, the general use case does not include a desktop environment.  You can control your VMs over SSH using the terminal.

Why do you need a desktop environment?  Your task would be easier -- not to mention less costly in terms of processing overhead -- without a DE.

---

### Post by TheFu on 2021-08-13
> **sniper8752 said:**
> I have virtualbox installed, and want to control my VMs.

**vboxmanage** - isn't that the command? [https://www.virtualbox.org/manual/ch08.html#vboxmanage-intro](https://www.virtualbox.org/manual/ch08.html#vboxmanage-intro)

If you used KVM + libvirt, then you could use **virt-manager** from any system with SSH to have a GUI to control all VMs on the host and built-in console support and provide SPICE-based remote desktop access using **virt-viewer** to any non-admins. SPICE is the fastest remote desktop available today.  

I think libvirt might work with virtualbox, but I haven't used it in so long as to know authoritatively. 
[https://www.virtualbox.org/ticket/1019](https://www.virtualbox.org/ticket/1019) is the closed ticket for vbox to support libvirt. Appears they aren't interested.  Xen, QEMU, KVM and many Linux containers are managed through virt-manager these days.

[https://virt-manager.org/](https://virt-manager.org/) lets you see what you are missing. 

KVM is the enterprise-grade hypervisor, but they've made it as easy to use as vbox thanks to virt-manager's GUI.  Migrating .vdi files from vbox into kvm isn't hard either. I don't think you need to do much besides copy the vdi files over, setup the VMs with similar hardware, then boot.  Migration of Linux is much easier than Windows. With Windows, there's a pre-migration step to remove drivers and tell Windows it is being relocated.  sysprep?  Something like that?  [https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/sysprep--generalize--a-windows-installation](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/sysprep--generalize--a-windows-installation) Yep. That's it.

---

### Post by ActionParsnip on 2021-08-14
> **sniper8752 said:**
> I have virtualbox installed, and want to control my VMs.

Yes. But to achieve what? What will you be doing on the desktop once you get connected?

---

