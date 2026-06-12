---
title: "Seamless Virtualization Help - VMware - How do I configure host-only networking?"
date: 2007-11-27
forum: Desktop Environments
---

### Post by TonySmash on 2007-11-27
Alright, I tried to follow the instructions listed here [https://help.ubuntu.com/community/SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization") as best as I could, but the only part that confuses me is the first part about setting up host-only networking. It says:

If using VMware, configure host-only networking, and note the VMs IP address for later.

Okay, so I go into the virtual machine settings and under Network I choose host-only...now what? How am I supposed to find the IP address of the VM? I know, it sounds like a silly question, but please humor me. I'm new to this and it seems like every time I try it (and yes, I've tried this many times), I break it somehow and end up completely bungling my host system's network. 

Then, a little bit farther down, it tells me the rdesktop command to use:

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p password
```

So, where it says IP of VM, I put the IP address I found earlier (which I was never able to find anyway...), and then there's that port, 3389 - do I need to change that at all or should I just leave it?

And one last thing -

Should I install VMWare Tools or will that mess up the seamless virtualization?

---

### Post by benner on 2008-01-14
I have been at this for a few days and have looked over all the posts i could find.  i still can't get past this:

ben@RAMEN-UBUNTU:~$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 192.168.31.128:3389 -u administrator -p password
Autoselected keyboard map en-us

and eventually...

ERROR: connect: Connection timed out


as a few other posts suggested, i changed double quotes to single ones, changed the login/password to the one i use, tried 'localhost' instead of the IP, put the user and password in quotes.  i turned off the firewall, the antivirus, the router's firewall.  all nothing.  please, any suggestions would be helpful.  i hate to give up after so much time but... i only have so much time.  thanks in advance...

btw, i am using vmware-server, xp pro is 32, ubuntu is 64 gutsy

xp can ping ubuntu host but ubunu ping to xp gets:

ben@RAMEN-UBUNTU:~$ ping 192.168.31.128
PING 192.168.31.128 (192.168.31.128) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

(and i guess this should probably be moved to the 'virtualization' forum.  i don't know how to do that.  i did a search and added my comments before i noticed.)

---

### Post by gentleStu on 2008-02-04
Hi there,

it's not a direct answer to your question, about how to configure host-only networking - but assuming you just want to run seamless Virtualization, I worked around this problem by switching to 'Bridged Networking'. 

I'd better stress I'm no networking guru - I've just stumbled through this myself - but I had pretty much the same symptoms  (using VMWare Server 1.0.3 with a Windows XP Pro guest VM) described by benner, and fixed them like this:

1) found the IP address of my Ubuntu host by doing 

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:B7:79:37:57  
          inet addr:**192.168.0.13**  Bcast:255.255.255.255  Mask:255.255.255.0
...
```

(it's the bit I've highlighted in bold: mine is 192.168.0.13)

2) found the default gateway of my Ubuntu host by doing
```

~$ ip route show | grep default
default via **192.168.0.1** dev eth0 

```

(it's the bit I've highlighted in bold: mine is 192.168.0.1)

3) found the DNS Server address used by my Ubuntu host by doing

```

~$ nslookup [www.google.com](www.google.com) | grep Server
Server:         **192.168.0.1**

```

(again, the bit highlighted in bold. Mine is 192.168.0.1)

4) found an unused IP address on the subnet of the Ubuntu host. There must be a better way of doing it, but I just guess a different number between 1 and 128 for the end of the IP address and ping it. If you get a response, guess again! If you get "Destination Host Unreachable", you can safely use that address - note it down for use later. E.g. 

```

~$ ping -c 3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.19 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.842 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=84.2 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.842/28.768/84.273/39.248 ms

 ~$ ping -c 3 192.168.0.128
PING 192.168.0.128 [noparse](192.168.0.128)[/noparse] 56(84) bytes of data.
From 192.168.0.13 icmp_seq=1 Destination Host Unreachable
From 192.168.0.13 icmp_seq=2 Destination Host Unreachable
From 192.168.0.13 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.128 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
, pipe 3

```

(so 192.168.0.128 is good for me)

5)  logged into the guest VM, and set its IP address to a fixed one on the same subnet as the host. I did this via Start Menu > Control Panel > Network Connections > (right click, choose Properties of) Local Area Connection > select 'Internet Protocol (TCP/IP)' and click Properties then:

i) checking the radio button to 'Use the following IP address'
ii) entering the IP address you got from step 4
iii) enter the subnet mask as 255.255.255.0
iv) entering the default gateway the same as you got from step 2
v) checking the radio button to 'Use the following DNS server addresses'
vi) entering the Primary DNS Server address that you got step 3

then click OK to close the sub-dialog box, and OK to close the main dialog box so the changes are saved.

6) shut down within the guest VM, then click on 'Edit virtual machine settings' for the guest VM. In the hardware tab, click on the Ethernet device, then change the Network Connection radio button to 'Bridged' and click OK.

7) restarted the guest VM, and from your terminal try the rdesktop command again:

```

~$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 192.168.0.128:3389 -u administrator -p password

```

(substituting the address you got from step 4 for 192.168.0.128, and the username/password details as appropriate)

... and that worked for me :)

There look to be other glitches that still make this not exactly it not exactly 'Seamless' - launching multiple apps, quitting from them gracefully etc. (I'm still wrestling with these!) - but hope this gets you over this hurdle...

good luck!

Stuart


ps to TonySmash: 

1) yes, leave the port as 3389: it's the default port used for communicating with Terminal Server.
2) yes, install VMWare Tools - though I don't think they'll help with your networking problem. They're good for all sorts of other reasons - see [http://www.petri.co.il/virtual_install_vmware_tools.htm](http://www.petri.co.il/virtual_install_vmware_tools.htm).

---

