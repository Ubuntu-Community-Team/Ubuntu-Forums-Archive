---
title: "openvpn client problems, works fine in windows."
date: 2010-04-16
forum: Desktop Environments
---

### Post by Pro_D on 2010-04-16
I have been having trouble getting openvpn client working in ubuntu 9.04.

From the windows side I run the GUI, right click, click connect, get a connection that has IP address and everything just works fine.

From the ubuntu side the network manager seems to be unable to connect, kvpnc doesn't seem to work...  Manual seems to have the most progress so I have been pursuing that.

If I sudo openvpn client.ovpn the last line before no further text output is a successful connection.  I then leave that cli window open and open a new one to try further troubleshooting.

The output of ifconfig tap0 though shows no IP (ipv4 network) address, also apparently no DNS server information is picked up.

The server is configured such that DHCP-server handles openvpn clients (relies on the fact that windows based clients have an identifiable mac address pattern).

Problem is that the linux client doesn't seem to be picking up DHCP information, even if it is the wrong info.  I already fixed the problem of linux openvpn randomly assigning mac addresses while the windows version is... less random.

Just to make sure the tunnel was working I used something like 'sudo ifconfig tap0 <ipaddress> up' to assign tap0 a valid IP and was able to ping machines by IP address over the tunnel.

To be honest I don't really know how to force DHCP communications on a particular interface.  Either the interface is configured in /etc/networking/interfaces or network manager handles it.  tap0 though is a dynamically generated interface NOT handled by either.

I tried sudo dhclient -r tap0 and the output suggested that it tried but it was no good, still no dynamic IP address nor dns information.  Also ifup tap0 says something about the device not existing.

<shrugs> I seem to be getting the tunnel fine but with no dhcp auto configuration it's just not all that useful in this state.

My laptop is a little dead at the moment so I don't have access to it's precise output or the complete config file but my configuration doesn't vary much from the client config file linked below:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

I think the only extra line I have is something along the line of 'lladdr 00:ff:cc:dd:ee:ff' in the client.ovpn file.

The only thing I can think of atm is to compile from the latest downloadable version (as the windows client is the latest from the site).  The ubuntu software (for both client and server) are from the repos which were built back in April or March of '09.

[edit]
ok, got it working.  I spent yet more time with google and got lucky this round...

Got my extra info from [http://hans.fugal.net/blog/2009/01/06/putting-openvpn-in-its-place/](http://hans.fugal.net/blog/2009/01/06/putting-openvpn-in-its-place/)

Basically edit your /etc/network/interfaces file:
iface tap0 inet dhcp
    hostname <your computer's name>
    client <your computer's name>

create an up.sh and down.sh script.

up.sh:
#! /bin/bash
ifdown tap0 2>/dev/null
ifup tap0 &

down.sh:
ifdown tap0

and finally in the client.conf (or client.ovpn) file, below the 'dev tap0' line add:
up "/etc/openvpn/up.sh"
down-pre
down "/etc/openvpn/down.sh"

You may get an error about external scripts, to fix this add in the following line (client.conf):
script-security 2

That will lower the security level of the openvpn client so that it can call external scripts...  (not sure of a way around this, for the moment I don't care considering it took 2 or 3 weeks to get it working in linux but 5 seconds in windows).

Also if you are assuming some windows client, who should always have mac addresses starting with 00:ff, which you can use to setup special dhcp settings for them in dhcp3-server... you will want to add this following line to make the linux openvpn client 'look' right.
lladdr 00:ff:aa:bb:cc:dd

where aa, bb, cc, dd can be any hex number but the 00:ff should not be changed, so 'lladdr 00:ff:01:23:45:6f' is valid as the first 2 hex values are 00 and ff.

With this I was able to ping and access resources within my network just as if I had plugged right in or used the windows openvpn client.

happy vpn-ing
[/edit]

---

