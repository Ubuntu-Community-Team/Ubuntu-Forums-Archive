---
title: "Ubuntu VMware no network."
date: 2006-04-06
forum: Desktop Environments
---

### Post by reefland on 2006-04-06
I've installed ubuntu many times, but never under VMware Server (Beta 2) (as a guest OS).  The host OS is XP Pro on a Dell Latitude D610 laptop with working wireless network connection.

The ubuntu install was clean, no warnings about a missing network or problems with DHCP.  System boots up fine, everything looks normal.. except no network services.  

In VMware Server Console, for the ubuntu profile I have it set for "Ethernet Bridged".

In ubuntu network configuration (via gui), the adapter for eth0 is marked as disabled.  I click the Admin mode button, the border turns red and then nothing happens.  A few second later the screen return as if I never pressed the admin button.

I don't have an error message.  I'm not sure what would be helpful to include here.   If you need some more information, feel free to ask.

---

### Post by hw-tph on 2006-04-07
Try enabling the interface in a console instead. If your network is already configured, **sudo ifup eth0** should bring the interface up.

You may also want to have a look at the FAQs on the VMWare site. I know there is some problems with Linux as the host OS when you have a wireless network - perhaps the opposite is true as well?


Håkan

---

### Post by reefland on 2006-04-07
[QUOTE=hw-tph]Try enabling the interface in a console instead. If your network is already configured, **sudo ifup eth0** should bring the interface up.
[/QUOTE]

[FONT="Fixedsys"]
Listening on LPF/eth0/<mac address>
Sending on LPF/eth0/<mac address>
Sending on Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
<I get several lines like this>

No DHCPOFFERS received.
[/FONT]

The network does have DHCP, the host OS is using it.

Here is the output of IFCONFIG.

[FONT="Fixedsys"]
eth0
Link encap: Ethernet HWaddr  <mac address>
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:2394 (2.3 KiB)
Interrupt:18 Base address:0x1400
[/FONT]

---

### Post by ColdFusion on 2006-04-07
Cool, thanks.  The **sudo ifup eth0 ** command worked.
How can I get this command to run every time I reboot?

---

### Post by reefland on 2006-04-07
I switched from bridged to NAT, rebooted.

ifconfig showed no eth0 information.

I then tried your command of "sudo ifup eth0".

DHCP worked and I'm on the network.

A) I'm not sure why this works.

B) how can I automate this to turn on eth0 on each reboot?

---

### Post by ColdFusion on 2006-04-09
[QUOTE=reefland]B) how can I automate this to turn on eth0 on each reboot?[/QUOTE]

Found it.!

from the command line...

[INDENT][FONT="Courier New"]**sudo vim /etc/network/interfaces**[/FONT][/INDENT]

...you should see the line...

[INDENT][FONT="Courier New"]**iface eth0 inet dhcp**[/FONT][/INDENT]

...add the following line before it...

[INDENT][FONT="Courier New"]**auto eth0**[/FONT][/INDENT]

If you want a static IP address change the word [FONT="Courier New"]**dhcp**[/FONT] for the word [FONT="Courier New"]**static**[/FONT] and add the following lines below it...

[INDENT][FONT="Courier New"][B]address 192.168.0.300
netmask 255.255.255.0
gateway 192.168.0.1[/B][/FONT][/INDENT]

...changing the address accordingly.

CF

---

