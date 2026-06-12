---
title: "FC9 in VirtualBox Resolution issue"
date: 2008-07-03
forum: Fedora/RedHat and derivatives
---

### Post by lheinemann on 2008-07-03
I am running FC9 in VirtualBox on Vista Business (company system no choice on running Windows).  Fedora installs just fine and runs great only I cannot get it to set to the correct resolution.  I am running a Dell D630 with a Quadro NVS 130 card and the screen runs at 1440x900.  When I go into System > Admin > Display I can change the configured display to 1440x900 but after restarting X I don't get the option to set to that resolution only 1280x1024.  I have noticed that on a shutdown or restart, it goes to the local login and then gives an error:

nm-system-settings: Could not get the system bus. Make sure the message bus daemon is running!  Message:Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

Also, now that the display is set to 1440x900 it won't let me change it.  I have tried configuring as 1600x1200 and higher and after restart still is 1440x900.  The video card that it shows is: Innotek Systemberatung GmbH VirtualBox Graphics Adapter.  If I try to change it to anything else it won't start X at reboot and I have to reset it at the command prompt.  

Any suggestion?!  Please help.

---

### Post by Kingsley on 2008-07-03
Install Vbox Additions. It might the easy solution.

---

### Post by RebounD11 on 2008-07-04
> **lheinemann said:**
> I am running FC9 in VirtualBox on Vista Business (company system no choice on running Windows).  Fedora installs just fine and runs great only I cannot get it to set to the correct resolution.  I am running a Dell D630 with a Quadro NVS 130 card and the screen runs at 1440x900.  When I go into System > Admin > Display I can change the configured display to 1440x900 but after restarting X I don't get the option to set to that resolution only 1280x1024.  I have noticed that on a shutdown or restart, it goes to the local login and then gives an error:

nm-system-settings: Could not get the system bus. Make sure the message bus daemon is running!  Message:Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

Also, now that the display is set to 1440x900 it won't let me change it.  I have tried configuring as 1600x1200 and higher and after restart still is 1440x900.  The video card that it shows is: Innotek Systemberatung GmbH VirtualBox Graphics Adapter.  If I try to change it to anything else it won't start X at reboot and I have to reset it at the command prompt.  

Any suggestion?!  Please help.

Inside VirtualBox you can't get Fedora to interact with your hardware, it interacts with your emulated system. That system's video card is the "Innotek Systemberatung GmbH VirtualBox Graphics Adapter". Installing Guest additions is a good advice since it will improve the overall functionality of the virtual machine, but don't expect 3D inside a VM just yet (VMware is working on sth like that, but I'm not sure if it's even beta already - with VMware workstation 6.5 beta I could have wobbly VM windows if I used Unity (seamless mode) on an WinXP guest inside a Fedora 9 host).

So I would say don't try to change the graphics adapter because it won't work, that's the correct one. As for the dbus error, that seems to be related to the network connection. Do you have network/Internet access from inside the VM, and do you have a network adapetr assigned to it (check that via VM setting - Network tab)? if you don't Guest adition should solve that to, if you do try a Google search for that problem or maybe on Innotek's website.

Hope this helps. Good luck!

---

