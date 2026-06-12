---
title: "Ubuntu, winxp and ATA Over Ethernet (AOE)"
date: 2009-03-04
forum: General Help
---

### Post by tinkerbox on 2009-03-04
Hi,

I been looking for complete tutorial on google for 2 weeks and found only advance tutorial for this. I'm completely newbie for linux, follow many tutorial but I never get out of the tunnel :(. I started with redhat, then centos and now I'm sticking on Ubuntu.

I been trying this on vmware. I'm trying to run winxp using physical hdd, not image. My steps are:

1. Install window xp and complete the tutorial: [http://etherboot.org/wiki/sanboot/winxp](http://etherboot.org/wiki/sanboot/winxp)
2. Install ubuntu 8.10 desktop, do updates, install dhcp
3. Copy vmware hdd to ubuntu vmware folder, and add this as 2nd hdd
4. Configure DHCP, working fine:
```

ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

#eth0 inet dhcp;
option routers 192.168.28.1;

subnet 192.168.28.0 netmask 255.255.255.0 {
    range 192.168.28.10 192.168.28.50;
}

filename "";
option root-path "aoe:e0.0";

```
5. install aoetools, do i need to configure anthing?
6. Install vblade, edit /etc/vblade.conf:
```

# /dev/sda1 is window xp hdd
eth0 0 0 /dev/sda1

```
7. Create another vmware client, and boot it using etherboot (gpxe ISO image), I manage to get DHCP ip and it stop there. Please see the attachment 


Found this: [https://help.ubuntu.com/community/ATAOverEthernet](https://help.ubuntu.com/community/ATAOverEthernet)
But does help me :(

It anyone know how to do this on ubuntu, please help me to fix this. Im sure this will help many other newbie out there :)

---

### Post by tinkerbox on 2009-03-16
First problem solved. I make a silly mistake in vblade.conf 
I will post the detail to make this works based on what I have posted above.

Note: I'm trying to run windows xp using AOE and setup ubuntu-8.10-desktop-i386 as target machine. Windows xp is run using physical(vmware) disk not image file. This test is runs on vmware.

target machine need to installed with: dhcp server, vblade, tfpt server (if you using image file)

dhcpd.conf
```
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

option routers 192.168.28.1;

subnet 192.168.28.0 netmask 255.255.255.0 {
	range 192.168.28.10 192.168.28.20;
}

# gPXE-specific encapsulated options
#
option space gpxe;
option gpxe-encap-opts code 175 = encapsulate gpxe;
option gpxe.priority code 1 = signed integer 8;
option gpxe.keep-san code 8 = unsigned integer 8;
option gpxe.no-pxedhcp code 176 = unsigned integer 8;
option gpxe.bus-id code 177 = string;
option gpxe.bios-drive code 189 = unsigned integer 8;
option gpxe.username code 190 = string;
option gpxe.password code 191 = string;
option gpxe.reverse-username code 192 = string;
option gpxe.reverse-password code 193 = string;
option gpxe.version code 235 = string;
  
# Other options that may be useful
#
#option iscsi-initiator-iqn code 203 = string;

filename "";
option root-path "aoe:e0.0";

```

No need to install aoetools on target machine! Install vblade, edit /etc/vblade.conf:
```
# /dev/sda is window xp hdd
eth0 0 0 /dev/sda
```

I make a mistake in vblade.conf
I entered **/dev/sda1**, it should be this >> **/dev/sda**
Fixed this and it works

If you start vblade service and its failed:
```
/etc/init.d/vblade start
```
you need to do this first then try again:
```
mkdir /var/run/vblade
```


Now I have a new problem. I tried to runs 2 windows xp machine (or more) using AOE at the same time. It works, both machine able to run and I can lunch any program on both machine. But both machine is using the same name (duplicate name)! Is there a way that I can assign windows xp hostname using DHCP(like assign ip address)?

Or any other way that you can think will fix this? I know this is possible but I have no idea yet how to do this...
Please help :D

---

### Post by tinkerbox on 2009-03-16
No one? ](*,)

Did I post this in wrong forum?

---

### Post by crokett on 2009-03-16
> **tinkerbox said:**
> First problem solved. I make a silly mistake in v

Now I have a new problem. I tried to runs 2 windows xp machine (or more) using AOE at the same time. It works, both machine able to run and I can lunch any program on both machine. But both machine is using the same name (duplicate name)! Is there a way that I can assign windows xp hostname using DHCP(like assign ip address)?



Yes, with a specialized DHCP server and client configuration.  Google is your friend.

 I wish I'd had that several years ago.  In a former job I wrote some software that would pull a previously created Windows image down from a server and apply it to a hard drive, then reboot the system locally.  Not quite what you are doing, but close. Your problem is the hostname is part of the donor image you are using.   It would have made my life a LOT easier if the hostname could be applied dynamically.  I had to play games with netsh and run a script at the first boot to set the hostname to something unique.  You would probably have to do something similar, however this would require a 2nd reboot once the hostname is changed and since you are booting over ethernet, this would of course put the old hostname back....

---

### Post by tinkerbox on 2009-03-16
Thank you for your reply :)

I read man for dhcpd.conf and there is option where DHCP server can assign the hostname to the client. 

[http://docstore.mik.ua/orelly/networking/tcpip/ch09_05.htm](http://docstore.mik.ua/orelly/networking/tcpip/ch09_05.htm)
```
get-lease-hostname

    Directs dhcpd to provide a hostname to each client that is assigned a dynamic address. Further, the hostname is to be obtained from DNS. This parameter is a Boolean. If it is set to false, which is the default, the client receives an address but no hostname. Looking up the hostname for every possible dynamic address adds substantial time to the startup. Set this to "false". Only set this to true if the server handles a very small number of dynamic addresses.
```

My biggest question is, how to make windows xp to accept hostname assign from DHCP?

---

### Post by saeraphas on 2010-10-06
I know this is an old topic, but I'm adding this in case it helps someone else.

There's not a built-in function in Windows XP to inherit the computer name from DHCP, as far as I know. It CAN be done with a vbscript, though. I wrote one that you could probably adapt to your purpose that you can find here: 

[http://www.douglashammond.com/resources/DHCP_hostname_changer.vbs](http://www.douglashammond.com/resources/DHCP_hostname_changer.vbs)

It's ugly and clunky, and but it worked for me. If you have any feedback or improvements on it, I'd like to hear from you.

---

### Post by maxchock on 2010-12-25
> **saeraphas said:**
> I know this is an old topic, but I'm adding this in case it helps someone else.

There's not a built-in function in Windows XP to inherit the computer name from DHCP, as far as I know. It CAN be done with a vbscript, though. I wrote one that you could probably adapt to your purpose that you can find here: 

[http://www.douglashammond.com/resources/DHCP_hostname_changer.vbs](http://www.douglashammond.com/resources/DHCP_hostname_changer.vbs)

It's ugly and clunky, and but it worked for me. If you have any feedback or improvements on it, I'd like to hear from you.

Is the script loaded during startup so the there is no need for a PC restart?

---

### Post by maxchock on 2010-12-25
> **tinkerbox said:**
> Thank you for your reply :)

I read man for dhcpd.conf and there is option where DHCP server can assign the hostname to the client. 

[http://docstore.mik.ua/orelly/networking/tcpip/ch09_05.htm](http://docstore.mik.ua/orelly/networking/tcpip/ch09_05.htm)
```
get-lease-hostname

    Directs dhcpd to provide a hostname to each client that is assigned a dynamic address. Further, the hostname is to be obtained from DNS. This parameter is a Boolean. If it is set to false, which is the default, the client receives an address but no hostname. Looking up the hostname for every possible dynamic address adds substantial time to the startup. Set this to "false". Only set this to true if the server handles a very small number of dynamic addresses.
```

My biggest question is, how to make windows xp to accept hostname assign from DHCP?

Is over a year after your post, have you found any good solution? I'm facing the similar problem and i'm stuck.

---

