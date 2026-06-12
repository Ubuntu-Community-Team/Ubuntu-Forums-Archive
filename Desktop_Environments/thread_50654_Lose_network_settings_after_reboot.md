---
title: "Lose network settings after reboot"
date: 2005-07-20
forum: Desktop Environments
---

### Post by linzer on 2005-07-20
A quick background.

I'm dual booting Win2k and Kubutnu Hoary with an Athlon 3200 MSI K8N Neo2 Platinum motherboard.  This nForce 3 motherboard has 2 built in NICs: a nVidia and a RealTek.  I'm using the nVidia NIC with a Win2k3 DHCP server.  I run the i386 build as apposed to the amd64 because I found a bunch of things I wanted weren't available with the amd64 route (w32 codecs, java, etc).

I get similar results using plain old Ubuntu but can resolve them under the Gnome config options.  With Kubuntu it no luck.  Here's what I'm seeing.

After initial install and login, everyting is fine.  The first time I reboot for whatever reason (update or booting into Win2k) and then go back into Kubuntu, I lose my network settings.  The first hint at boot time, is the clock can't set its time from the NTP server.  Upon logging in trying to ping a network results in a "network unreachable" error.

I can't set eth0 (the nVidia NIC) active in kcontrol even if from a terminal session I "sudo kcontrol".  Same result if I give the NIC a static IP address.

I've tried installing a couple of different times and see the same results.  The first time I thought it was because I was updating the kernel.  This past time I did no updates and saw the same results.  As I stated, I see similar results with ubuntu but prefer to run kubuntu.  In gnome (under a ubuntu install) I can use the network widget to activate the NIC after a reboot.  No such luck in kubuntu.

I've tried searching the forums without much luck.  Any suggestions without having to reinstall yet again?

TIA

---

### Post by amohanty on 2005-07-20
What does ifconfig return:
>> ifconfig

If you have only one NIC  and it is active it should return something like:

eth0      Link encap:Ethernet  HWaddr 00:11:D8:BA:D5:AF
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feba:d5af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:52040074 (49.6 MiB)  TX bytes:6752975 (6.4 MiB)
          Interrupt:23

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1647502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1647502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:185157155 (176.5 MiB)  TX bytes:185157155 (176.5 MiB)

---

### Post by linzer on 2005-07-21
[QUOTE=amohanty]What does ifconfig return:
>> ifconfig

If you have only one NIC  and it is active it should return something like:

eth0      Link encap:Ethernet  HWaddr 00:11:D8:BA:D5:AF
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feba:d5af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:52040074 (49.6 MiB)  TX bytes:6752975 (6.4 MiB)
          Interrupt:23

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1647502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1647502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:185157155 (176.5 MiB)  TX bytes:185157155 (176.5 MiB)[/QUOTE]


Yesterday when I first posted this message I had my lopback and eth0 entries there.  The eth0 entriesd were missing the IPv4 (inet) address information though.

Today, when i log in, ifconfig returns nothing.

As sated, in my original post, this motherboard has 2 built in NICs.  I'm using the nVidia NIC and not the RealTek.

I have copied all log files from /var/log and subfolders.  If there is something that might help determine why my network is all hosed up should I be looking there?

Thanks again.

---

### Post by linzer on 2005-07-21
FWIW, I went through my log files.  In syslog when the sytem first comes up good, I have the following entry.

Jul 19 21:37:21 net/ddetect.hotplug: Detected hotpluggable network interface eth0

Later a bunch of DHCP logs

Jul 19 21:37:34 dhclient: Internet Software Consortium DHCP Client 2.0pl5
Jul 19 21:37:34 dhclient: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Jul 19 21:37:35 dhclient: Listening on LPF/eth0/00:11:09:93:58:14
Jul 19 21:37:35 dhclient: Sending on   LPF/eth0/00:11:09:93:58:14
Jul 19 21:37:35 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jul 19 21:37:35 dhclient: DHCPOFFER from 192.168.1.20
Jul 19 21:37:37 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jul 19 21:37:37 dhclient: DHCPACK from 192.168.1.20


Upon the failed reboot I don't have any reference to the hotplug eth0 interface being found.

---

