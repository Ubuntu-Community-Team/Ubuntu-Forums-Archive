---
title: "Nautilus 2.12.1"
date: 2006-06-18
forum: Desktop Environments
---

### Post by eugenia on 2006-06-18
Can anyone help with a Nautilus 2.12.1 graphical shell for GNOME issue?

I cannot get Nautilus to detect computers on my LAN.

This is really causing me grief when it comes to weaning the family off Windows!


A bit long winded but to explain the situation:-

I have a small home network (cable not wireless) presently made up of 2 desktops and a laptop.

Desktop 1 dual boots Ubuntu 5.10 and Windows ME. It is the 'server' in that it has two ethernet cards (ETH0 connected to the internet and ETH1 connected to my LAN with a static address 192.168.0.1)

Desktop 2 dual boots Ubuntu 6.06 and Windows ME. (I just upgraded it from 5.10 with a clean CD install and the problem was present before the upgrade) This desktop has a static address 192.168.0.3.

The laptop has Windows ME only and I have assigned it a static address 192.168.0.10.

I use Firestarter on Desktop 1 but I don't think it has any bearing on my problem as it persists even after removing the package with Synaptic.

The physical setup is:-

outside world > ADSL modem > ETH0 Desktop 1 > ETH1 Desktop 1 > 8 port switch > Desktop 2 and Laptop.

When all computers are booted with Windows they can access the internet, see each other and share files i.e. the physical setup works.

If I then boot Desktop 2 with Ubuntu, Desktop 1 and the Laptop can still see each other and share files but they cannot see or access Desktop 2. Remember my 'server', Desktop 1, is still booted with Windows ME. If I go into Places > Network Servers > Windows Network, Desktop 2 can (quickly) see and transfer files from Desktop 1 and the Laptop. All computers can ping each other.

(I am not concerned that the ME boxes cannot see Desktop 2 at this stage as I hope eventually to sort this out when I have time to get a better appreciation of Samba)

When I boot Desktop 1 with Ubuntu and have Desktop 2 and the Laptop run on Windows the two ME computers can see each other and share files but when I go into Places > Network Servers on Desktop 1 nothing shows up (after a long wait).

Most frustrating of all is when both Desktops are booted to Ubuntu, in the case of both computers Nautilus will not detect the other Ubuntu box (or anything else for that matter).

Regardless of any senario/combination of operating systems all computers can ping each other and access the internet.

It is unlikely that there is a problem with Nautilus so I am wondering if there is something I have missed in the documentation or I have to do to something to configure Nautilus to work in my case.

Can anyone suggest a possible solution or link to further reading. There appears to be no reference to home networking or LAN in the Wiki or maybe I am using the wrong terminology.

---

