---
title: "Virtualbox 2.1.2 headless on Ubuntu 8.10 Server"
date: 2009-02-01
forum: General Help
---

### Post by fieldyweb on 2009-02-01
I'll preceed this with the comment, i'm not a novice Ubuntu user, however, having spent all day following various instructions on Howtoforge, Ubuntugeek and various other sites.. i come to an impass

I am trying to do the following:

HOST PC

Running Ubuntu 8.10 Server and static IP of 192.168.1.2
No GUI.. just plain old text console.

I'd like to run Virtualbox 2.1.2 on this server, and have 3 different "Guest" OS's running on the abov host.

Each one will pick up its IP not from the default NAT, but from the HOST's network.

So as far as i'm concerned i have 4 different PC's on my network.


I have got Virtualbox 2.1.2 installed, and have got the static ip of the host  and followed the instructions at 
[URL="http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server"]
http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server[/URL]

However i cannot for the life of me figure out from the command line how to launch my first virtual machine and have it pick up its IP from the main network..

if i run

> VBoxManage modifyvm "Ubuntu 8.04 Server (mail)" -nic1 hostif

it runs with no errors

however when i run

> VBoxHeadless -startvm "Ubuntu 8.04 Server (mail)"

i get the error message back
> 
VirtualBox Headless Interface 2.1.2
(C) 2008-2009 Sun Microsystems, Inc.
All rights reserved.

Listening on port 3389
Error: failed to start machine. Error message: Failed to open/create the internal network 'HostInterfaceNetworking-' (VERR_INTNET_FLT_IF_NOT_FOUND).
Unknown error creating VM (VERR_INTNET_FLT_IF_NOT_FOUND)

And the virtual machine doesn't start..

I need to run virtualbox, as VMware 2.0 server runs like a dog, and times out, and OpenVZ isn't an option an eaither, i'd like to get this working headless on Virtualbox..

Any assistance appreciated.

---

### Post by fantakola on 2009-02-26
Make sure you have run: 

  VBoxManage modifyvm [vm-name] -nic1 hostif -hostifdev eth0

-obviously with the 'vm-name' and 'eth0' changed as appropriate.

---

### Post by angelot on 2009-11-29
I got this error when running the command:
```
$ VBoxManage modifyvm ubuntu-notebook -nic1 hostif -hostifdev eth0
VirtualBox Command Line Management Interface Version 3.0.12
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

error: Invalid NIC number ''
[1]+  Done                    VBoxHeadless -startvm ubuntu-notebook --vrdp on
```

btw: Running 9.10 server and VBox virtualbox-3.0_3.0.12-54655_Ubuntu_karmic_i386.deb from Sun...

---

### Post by meises on 2010-08-31
Hi

I had the same problem and solved it by declaring the appropriate interface:

vboxmanage modifyvm <myvmname> --bridgeadapter1 eth0

meises

---

### Post by mickwombat on 2010-08-31
Hi,
I've found the easiest way to setup to VMs on a headless host is to install them on a desktop system using the GUI and then export the VM.  Transfer it across to the server and then import it using the command which can be found in here somewhere. [http://dlc.sun.com.edgesuite.net/virtualbox/3.2.8/UserManual.pdf]("http://dlc.sun.com.edgesuite.net/virtualbox/3.2.8/UserManual.pdf")
Cheers

---

