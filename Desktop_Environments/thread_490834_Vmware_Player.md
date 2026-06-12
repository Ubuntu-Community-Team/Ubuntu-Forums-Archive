---
title: "Vmware Player"
date: 2007-07-02
forum: Desktop Environments
---

### Post by logreeval on 2007-07-02
I want to install VMware Player, I couldn't find it in the Synaptic so I downloaded the tar, un tarred it and now i cant get the vmware-install.pl to go, it says Command Not Found, what should I do?

I have the Virtual machine, i just need to install the Vmware PLayer now..

---

### Post by oldmanstan on 2007-07-02
add this:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
at the end of your /etc/apt/sources.list file, or go into synaptic do settings >> repositories >> third party >> add and enter that as the apt line

now update your repos and vmware server and player will be available

---

### Post by logreeval on 2007-07-02
I see, but Vmware Player TWO 2.0 is not on there :(

Is there any way to get that?

---

### Post by oldmanstan on 2007-07-03
not from a repo as far as i know

when you run the install script make sure you are typing it into a terminal like this (assuming you are in directory of the script):
```
./vmware-install.pl
```
if you just type vmware-install.pl is looking in your PATH and can't find any program by that name so you have to preface it with ./ to get it to look in the current directory, just checking

---

### Post by logreeval on 2007-07-03
thanks, I got it installed now.

I cant seem to get my printer USB to work in it?, do you know like how to enable it or something?

---

### Post by oldmanstan on 2007-07-03
from what i understand (i may be wrong) usb devices require that you buy vmware workstation.  if you want usb, you might try [virtualbox]("http://www.virtualbox.org/") instead as it supports usb and is open source (so it's free)

---

### Post by bobpaul on 2007-07-03
USB works in VMWare Player. FWIW, the VirtualBox website seems to imply you have to buy *their* full version to get USB, though I have little experience with VBox.

For USB and CDRom devices you have to select which devices you want to export to the host system. I'm having trouble getting VMWare up after an OS reinstall, so bare with me as it's from memory. 

Across the top of the application is the file menu bar. The second menu from the left should be called "Devices" I think. Click on that and find you're USB device. If it has a check box it's being exported to windows, so just give it a checkbox. It doesn't matter if you already have the device working in windows or not.

If you're USB device is not on the list, that's because it wasn't plugged in when you opened VMWare-Player. Close the player (either let it shutdown or suspend. I the player suspend it as it's faster), plug in the device, and then restart the player. Once it's back up, check the box and windows should think you just plugged something in.

---

### Post by logreeval on 2007-07-03
Hi, thanks for the reply.

The thing is, even if I do all of that, the USB thing still doesn't show under devices, I tried removing everything and just pluggin the printer cable and nothing, it doesn't show up on teh devices or anything :(

---

### Post by ayates on 2007-07-03
Do you have a 

usb.present = "TRUE"

line in your .vmx file ?

---

### Post by logreeval on 2007-07-03
Ill check..

---

### Post by logreeval on 2007-07-03
No i do not! :-\

Where should I put it?

---

### Post by logreeval on 2007-07-03
I got it, THANKS!

---

### Post by logreeval on 2007-07-04
Now, I have another problem!

It seems that the Vmware Accelerated PCNet connection is firewalled?

How can i get this internet connecton not firewalled?

---

### Post by bobpaul on 2007-07-04
Also, are you using bridged networking? This puts your guest on the same subnet as your host. NAT'd works just like a broadband router and is by nature a type of firewall. You wanted *ConnectionType = "bridged"*

Otherwise, maybe it's just the windows firewall getting in your way on the guest??

---

### Post by logreeval on 2007-07-04
I am in Ubuntu, running a virtual XP install.

I have it bridged. I don't know if this has anything to do, but I am using wireless connection.

---

### Post by bobpaul on 2007-07-04
It would make a difference if you're running something goofy like OpenWRT on your router, as crazy tinkerers running Linux on their PCs often do :D. Some routers separate (essentially firewall) the wireless clients from the wired clients and maybe even from each other, but I would think you'd know about that if it was happening.

To help us get a feel, post the output of 'ipconfig' from the windows command prompt. Also 'ifconfig' from the Ubuntu terminal.

Also, what service are you attempting to run in windows, and which machine is trying to connect to it? Finally, have you tried running connecting to services running on the Ubuntu host from that same client machine?

---

### Post by logreeval on 2007-07-04
I am just trying to connect to the internet in Vmware Player, but the connections shows there is a firewall on it.

I am running from the Ubuntu using the internet to post here, all I want to do in the Vmware XP.

Here is the first log

eth0      Link encap:Ethernet  HWaddr 00:14:22:AD:F0:A1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:13:02:9E:FB:AA  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe9e:fbaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88067 errors:60 dropped:4594 overruns:0 frame:0
          TX packets:58145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120197202 (114.6 MiB)  TX bytes:5278015 (5.0 MiB)
          Interrupt:17 Base address:0x2000 Memory:dfdff000-dfdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1596 (1.5 KiB)  TX bytes:1596 (1.5 KiB)

======================
and,...............

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . . . . :

---

### Post by bobpaul on 2007-07-05
Shows it's firewalled? You mean like this: [IMG]http://ubuntuforums.org/attachment.php?attachmentid=37370&d=1183644879[/IMG] ? If so, that only means that the Windows firewall is enabled, which shouldn't be causing this particular problem, though you would be safe in your case (since you're connecting behind a wireless router, and not directly to the Internet) to disable the windows firewall.

It seems WinXP isn't getting an IP address from your DHCP (router). Try configuring the ip address manually. In windows, right click the adapter and choose 'Properties'. Then double click on Internet Protocol (TCP/IP)' and set the following:
IP Address:           192.168.1.10
Subnet Mask:        255.255.255.0
Default Gateway: 192.168.1.1
Prefered DNS:       192.168.1.1

I'm not sure why DHCP isn't working for you, but I have a couple of ideas. Anyway, see if the static IP works. You may need to change 192.168.1.10 to something else if that address is already in use on your network.

---

### Post by logreeval on 2007-07-05
Ah, I got the firewall thing now.

But, I set it like you said and there is ZERO packets received, none. So it must be something weird...Since I set up the VM at a Wired connection and now I am trying to get it to work from a wireless have anything to do with it?

---

### Post by bobpaul on 2007-07-05
Yes. Yes, I think that's it. It was one of 3 suspicions I had, but now I'm quite certain after finding [this thread]("http://www.vmware.com/community/thread.jspa?threadID=41312") and doing some other googling.

Try executing 'ps aux | grep -i bridge' on the host. I'm willing to bet you'll see something that ends in "/dev/vmnet0 eth0". The eth0 is the device your virtual network adapter is bridged to (I wasn't entirely sure if that's how it worked before). You need to change that so it's bridged with eth1, your wireless device. You can do that by running the vmware config script again.

```
sudo vmware-config.pl
```
should ask you which adapter to bridge with. Be sure to say eth1.

Then you can go back and set your windows network to "Automatically Assigned" again.

**Edit:** I only have 1 NIC in my computer, so I had to make an assumption about the config script. It actually sounds like it automatically maps vmnet0 to eth0 and vmnet2 to eth1, etc. Just watch for the vmnet that's assigned to eth1 if it doesn't let you configure it. You **may** have to modify your vmx file once again, adding the following in place of 'connectionType - "bridged" '
```
ethernet0.connectionType = "custom"
ethernet0.vnet = "/dev/vmnet2" 
```

---

### Post by logreeval on 2007-07-05
I have both enabled. The eth1 only connects if I manually change the IP addresses like you said.

I dont really know what to do, are there any other things I could try?

---

### Post by bobpaul on 2007-07-05
> **logreeval said:**
> I have both enabled. The eth1 only connects if I manually change the IP addresses like you said.

I dont really know what to do, are there any other things I could try?

Huh, what? Sorry, what did you do and what's the current state of things? You lost me just now...

**Edit:** Oops, sorry. that last post should have read ethernet0.connectionType, etc. Please see my last post again, as re-edited.

---

### Post by logreeval on 2007-07-05
that worked!!!! :D

Now...what happens if I go to my wired network?, will this work at both places?

---

### Post by bobpaul on 2007-07-05
Well, each vmnet device is bridged to exactly 1 physical adapter, so if you want both in windows as well, you'll have to edit the vmx again.

 Simply copy/past the etheernet0.* entries and change them to ethernet1.* entries. Then you'd have to change the /dev/vmnet devic for ethernet1. This will give you "Local Area Connection" 1 and 2 in windows, and the one that's being used on ubuntu is what'll be used in windows (the other will have no connectivity, show cable disconnected or something)

---

### Post by logreeval on 2007-07-06
Cool, thanks.

---

