---
title: "Internet Connection, Sound Problems"
date: 2009-01-06
forum: General Help
---

### Post by SivaShankari on 2009-01-06
Hi all,..

Im new to this forum. First i wud lyk to thank d ppl giving guidelines in this forum. Ive installed Ubuntu 8.10 Desktop edition. Im using Asus motherboard. Im using Dual OS. Ive installed device drivers for Windows, and things are smooth. But in Ubuntu, im unable to connect to internet and no sound too. Tried to access the 'interfaces' text document in /etc/network folder. But, im getting 'Permission Denied' error. To my knowledge, im the privileged user. ive not enabled any root user kind of thing. I request you guys to gimme some solution to this problem.

Thnx in advance.

---

### Post by gettinoriginal on 2009-01-06
Ubuntu by default creates a root user from the initial user, but locks it down so the initial user cannot accidentally corrupt the system.  May I suggest some reading here so that you may be able to better understand the Ubuntu system:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
After you read through that for info that you may need, then here is some sites for sound issues:
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506),
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012),
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
you do not specify your internet connection ie wireless, ethernet, or dialup, please do so and post it back for further help.  :P

---

### Post by SivaShankari on 2009-01-06
Hi...

Thanks alot for your fastest response.ll surely go thru those links. My connection is broadband through ethernet cable.its wired. Anything else i shd furnish??

Thanks in Advance..

---

### Post by gettinoriginal on 2009-01-06
System > Administration > Network Tools, is that configured properly ??

---

### Post by SivaShankari on 2009-01-07
Hello,

I checked with that Network Tools option. In 'Devices' tab, there are two choices. (1)Loopback (2) Ethernet

In the Loopback option, IP Mask, and some subnet mask value are all ok. 

In the Ethernet option, all the values are : *not available*

Hence, i feel like,its not configured properly. Well, here s d problem, ryt?? I think, vve to fix this thing..

Plz plz do help me. Its really tiresome, to shift for net connection to windows, and to ubuntu.

---

### Post by aesis05401 on 2009-01-07
Heya,

You mentioned that you are using an ASUS motherboard, but some additional information would be helpful. 

If the NIC is integrated into the motherboard then the model# for the mobo (or preferably a link to some chipset details) would help.

If the NIC is not on the mobo then please provide maker and model of the network card.

Also, searching for your NIC or mobo info and the word Ubuntu should pull up other posts related to issues with that hardware.

Here is a [helpful link]("http://www.linuxquestions.org/hcl/") as well.. though I should check - this forum might keep more specific compatibility lists for Ubuntu distros.

---

### Post by halovivek on 2009-01-07
> **SivaShankari said:**
> Hello,

I checked with that Network Tools option. In 'Devices' tab, there are two choices. (1)Loopback (2) Ethernet

In the Loopback option, IP Mask, and some subnet mask value are all ok. 

In the Ethernet option, all the values are : *not available*

Hence, i feel like,its not configured properly. Well, here s d problem, ryt?? I think, vve to fix this thing..

Plz plz do help me. Its really tiresome, to shift for net connection to windows, and to ubuntu.

Do you use Airtel or BSNL broadband connection?
whether the Internet provider given any IP address to you ?

---

### Post by SivaShankari on 2009-01-07
My motherboard details:

Asus P5SD2-VM

Im sorry, i couldnt find anymore information. Im trying to follow this thing:

[https://answers.launchpad.net/ubuntu/+question/38994](https://answers.launchpad.net/ubuntu/+question/38994)

Ive downloaded that patch.. ll give it a try..

Somewhere, i found like, changing the /etc/network/interfaces text. But i lost that snippet. Would that help?? What is that exactly??

---

### Post by SivaShankari on 2009-01-07
Im using BSNL Broadband connection..

using DHCP

So, IP will be dynamic, ryt??

Ive got this info. from my Windows Net connection properties.


Physical Address 00-22-15-C5-69-9F
IP Address       192.168.1.2
Subnet Mask      255.255.255.0
Default Gateway  192.168.1.1
DHCP Server      192.168.1.1
Lease Obtained   1/7/2009 1.31.58 PM
Lease Expires    1/8/2009 1.31.58 PM
DNS Server       192.168.1.1
WINS Server

---

### Post by halovivek on 2009-01-07
In network manager - select the connection as auto-echo and try. 
could you post some more details below.
code
1. sudo lshw -C network
2. ethtool eth0
3. ping -c 4 [www.google.com](www.google.com)
   ping -c 4 74.125.43.104
4. cat /etc/resolv.conf
5. cat /etc/network/interfaces
6. route -n

---

### Post by SivaShankari on 2009-01-07
Im trying to make some modifications in the files, as mentioned in the posts. But as im not logging in as the root user, im not able to access,or modify them. So, cant even give a try. Could anyone plz tell me, how to access /log in as 'root' user? I dint created any 'root' user account by myself. In the previous Ubuntu versions, it was mandatory, and I had one such account. But how to proceed with latest (8.10) version? Plz tell me.

Thanks for all those, trying to help me in fixing this problem. Hope something would work soon.

---

### Post by gettinoriginal on 2009-01-07
Alt F2 will bring up a box, type in "gksudo nautilus" without the quote marks, it will open your file browser as root.  :P

---

### Post by SivaShankari on 2009-01-07
Hello,

Ive tried the aforesaid commands, and the results are as follows:

**1. sudo lshw -C network**---------------------------------------
[sudo] password for maggi: 
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:22:15:c5:69:9f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full latency=0 link=no module=sis190 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:cf:91:a1:c3:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

.........................................
**2. ethtool eth0**----------------------------------------------------------
bash: ettthtool: command not found
maggi@ubuntu:~$ ethtool eth0
The program 'ethtool' is currently not installed.  You can install it by typing:
sudo apt-get install ethtool
bash: ethtool: command not found
"TRIED TO DO THE ABOVE THING, AND THE RESULT, AS FOLLOWS:"

maggi@ubuntu:~$ sudo apt-get install ethtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ethtool

----------------------------------------------------------
**3. ping -c 4 [www.google.com](www.google.com)**-----------------------------------------------------------
maggi@ubuntu:~$ ping -c 4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

----------------------------------------------------------------

**4. ping -c 4 74.125.43.104**---------------------------------------------------------------
maggi@ubuntu:~$ ping -c 4 74.125.43.104
connect: Network is unreachable

===============================================================

**4. cat /etc/resolv.conf**-----------------------------------
maggi@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

=================================================================

**5. cat /etc/network/interfaces**---------------------------------------------------------
maggi@ubuntu:~$ cat /etc/network/interfaces
auto lo  
iface lo inet loopback

=================================================================
**6. route -n**------------------------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
__________________

---

### Post by SivaShankari on 2009-01-07
Hi all,

I also tried to do that change in sis190.c file.. its not available in the specified location, that is - /lib/modules/(sm... generic)/kernel/drivers/net But no sis190.c is available. only sis190.ko is available. and, that is also cannot be opened using gedit.

Still struggggggggling :confused:

---

### Post by halovivek on 2009-01-07
1.can you post full configuration of your computer please?
code
can you type in terminal and post this one?
ifconfig
can you try this one also?
code
netstat -nr
sudo ip route add default via 192.168.1.1  
sudo route add default gw 192.168.1.1
sudo vi /etc/network/interfaces

Find eth0 or desired network interface and add following-
Code:

gateway 192.168.1.1

try and tell me.

---

### Post by SivaShankari on 2009-01-07
Hi, here r d results:

**maggi@ubuntu:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:22:15:c5:69:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

eth0:avahi Link encap:Ethernet  HWaddr 00:22:15:c5:69:9f  
          inet addr:169.254.7.91  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1012 (1.0 KB)  TX bytes:1012 (1.0 KB)
===================================================

**netstat -nr**
-----------------------------------------------------
maggi@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0
==============================================================
**sudo ip route add default via 192.168.1.1 **-------------------------------------------------
RTNETLINK answers: File exists
===========================================
**sudo route add default gw 192.168.1.1**--------------------------------------------
SIOCADDRT: File exists
=================================================
**sudo vi /etc/network/interfaces**-------------------------------------------------
auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1

~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/network/interfaces" 4 lines, 52 characters

=================================================

---

### Post by razar45 on 2009-01-07
I dont know whats wrong then....when you installed it...did  your computer already have internet connection???

---

### Post by SivaShankari on 2009-01-08
Hello...

Im having internet connection, and its working perfect in Windows. Initially, with windows i had device drivers problem, but after installing them, things went smooth. My motherboard is Asus.But, i dono wer d prob. lies exactly. Ive been trying to fix this, but its nt working properly. Ive found in some forums that, modifying that sis190.ko file will be feasible, but im not able to edit that file. Its not opening at all. How to modify that file, and recompile it?? Could anybody drop a word on it??

Thanks in well advance..

ITs really a cumbersome, brain-eating task guys.. Plz do throw a light....

---

### Post by halovivek on 2009-01-08
could you post full configuration of your system from Hard disk to mother board. Thanks

---

### Post by SivaShankari on 2009-01-08
Hard disk - 80 GB
RAM       -  1 GB
Mother Board - ASUS P5SD2-VM
Processor - INTEL

Using Dual OS

Windows XP  Internet Connection, sound everything perfect. 

Internet Connection - Ethernet, BSNL Broadband

Ubuntu 8.10 Desktop Edition - Sound is OK. No internet Connection.

Thanks..

Wen ll my prob. be solved ?/???

:(

---

### Post by halovivek on 2009-01-08
[QUOTE=

Wen ll my prob. be solved ?/???

:([/QUOTE]

Dont worry soon it will get solved. i had the same problem like this.

---

### Post by halovivek on 2009-01-08
you can check this thread for more
[http://ubuntuforums.org/showthread.php?t=1020426](http://ubuntuforums.org/showthread.php?t=1020426)

---

### Post by SivaShankari on 2009-01-09
My problem is not yet fixed, and im worn out. Thinking of re-installing the older version.

Thanks for all the kind-hearts, who tried to help me.

---

### Post by rvergara on 2009-02-22
Hi all,

Read this (and others) thread before buying a good deal for a new ASUS box with the ASUS P5SD2-VM motherboard with built-in SiS network adapter 191.

When I went for the box I asked a good old RTL 8139 PCI card to be installed. Cost for this additional was $6 . I installed Ubuntu 8.10, as anticipated the integrated network did not work but just to switch to the RTL 8139 and I was browsing in no time. I guess $6 was not worth the time I would have to spend to fix the issue. Hopefully 9.04 will solve the issue but in the meantime I am happy.

Regards

Ramiro

---

