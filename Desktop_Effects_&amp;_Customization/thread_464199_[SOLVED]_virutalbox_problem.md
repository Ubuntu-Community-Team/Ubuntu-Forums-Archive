---
title: "[SOLVED] virutalbox: problem"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by kris2pe on 2007-06-04
I get this error while executing virtualbox on my system 

Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

Need help thanks!!!

---

### Post by thelinuxguy on 2007-06-04
sudo chmod 0666 /dev/net/tun
sudo chmod 0666 /dev/vboxdrv

---

### Post by kris2pe on 2007-06-05
I still get the same error! HELP!!! 

When I enter the code I still get this as and error
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

when I restart the program I still get this as an error
Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED)

What next?

---

### Post by thelocust on 2007-06-05
I bet if you install it with automatix2 everything will work.

---

### Post by Kingsley on 2007-06-05
Did you reboot after you installed it?

---

### Post by thelinuxguy on 2007-06-05
Have you configured it for Bridge mode? The configuration may be incorrect. Check if it works under NAT.

Start VirtualBox
Select the virtual machine >> Details >> Networking
Under Adapter 0 >> Attached to, select: NAT
Make sure other adapters are not enabled.

Does it work now?

---

### Post by kris2pe on 2007-06-05
Thanks linuxguy it actually worked! :D

---

### Post by thelinuxguy on 2007-06-05
> **kris2pe said:**
> Thanks linuxguy it actually worked! :D
You are most welcome.

---

### Post by cofeineSunshine on 2007-07-30
this reply for those who experienced the same error but need host interface for reaching guest machines' servers

sudo tunctl -t tap0 -u <username>

---

### Post by thelinuxguy on 2007-08-17
> **cofeineSunshine said:**
> this reply for those who experienced the same error but need host interface for reaching guest machines' servers

sudo tunctl -t tap0 -u <username>

In addition, [ this post]("http://ubuntuforums.org/showpost.php?p=2723644&postcount=15") details bridge configuration for VirtualBox so that sharing works both ways. After the bridge is created using the script given in this post, use tap1 as the host interface in VirtualBox since the script has tap1 in it. And also assign a static IP to the guest OS. The guest OS will then be reachable via this IP.

---

### Post by dover19 on 2008-05-08
> **cofeineSunshine said:**
> this reply for those who experienced the same error but need host interface for reaching guest machines' servers

sudo tunctl -t tap0 -u <username>

sudo: tunctl: command not found

lol...wtf.

---

### Post by jurij on 2008-06-13
You need to install uml-utilities:
sudo aptitude install uml-utilities

Then you add yourself to uml-net group:
sudo adduser yourusername  uml-net

Logout and login again for permission to take effect
-------
be sure to have bridged interface in your /etc/network/interfaces
something like this:
# Network bridge
auto br0
iface br0 inet dhcp
    bridge_ports eth0
    bridge_fd 2.5

You can comment eth0 interface, because it will be no longer needed.
Also check your firewall rules to use br0 interface.
sudo /etc/init.d/networking restart    - for changes to take effect
If you want to use Virtual host interface in VirtualBox, you must create that interface first. To do that use this commnad:
sudo VBoxAddIF vbox0 yourusername br0

Now you can setup VirtualBox networking like this:
Attached to:
Host Interface

Interface Name:
vbox0

leave other fields empty, and thats all ;-)

PS:
...you can create scripts that automatically create interfaces for you in VirtualMachine start/stop and put them as Setup Application / Terminate Application... don't forget to post them here :) )

Good Luck

---

