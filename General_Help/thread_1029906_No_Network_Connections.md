---
title: "No Network Connections"
date: 2009-01-03
forum: General Help
---

### Post by Arukas on 2009-01-03
I just installed Ubuntu 8.10 on my Dell Inspiron 8200.  When I plug in the network cable from the cable modem.  The lights flash and it looks like it detecting it.  But when it is done, it just says "Network Disconneted"  Anyone know how to fix this problem?

---

### Post by Tim Sharitt on 2009-01-03
In a terminal run
```
lspci
```
and
```
lshw -C network 
```
and post the output of each.

---

### Post by Arukas on 2009-01-03
lspci

[PHP]
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
[/PHP]

sudo lshw -C network

[PHP]*-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:bb:57:51
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:49:22:64:5a:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/PHP]

---

### Post by Loosewheel on 2009-01-04
> **Arukas said:**
> I just installed Ubuntu 8.10 on my Dell Inspiron 8200.  When I plug in the network cable from the cable modem.  The lights flash and it looks like it detecting it.  But when it is done, it just says "Network Disconneted"  Anyone know how to fix this problem?

If you right click the 'Network Monitor Applet' in the panel, is the "Enable Networking" box checked?

---

### Post by Arukas on 2009-01-04
Yes it is checked.

---

### Post by Loosewheel on 2009-01-04
Arukas, did you get your network up? If not, post your '/etc/network/interfaces' file.

---

### Post by Arukas on 2009-01-04
No I did not get my network working.

It says:

auto lo
iface lo inet loopback

---

### Post by Loosewheel on 2009-01-04
> **Arukas said:**
> No I did not get my network working.

It says:

auto lo
iface lo inet loopback

Maybe have a look at 'man interfaces' from a console.
It says this is the file that 'ifup' uses for config info.
Maybe: 
auto eth0
iface eth0 inet dhcp
might work. (If your running dhcp)

I am just guessing here. That man page isn't real clear to me.
Perhaps someone with some knowledge will jump in.

---

### Post by leedsdevil on 2009-01-04
did you try turning off both your cable box and your computer? if not try that let it reset your IP

---

### Post by Arukas on 2009-01-04
Already tried that, more than once.  I think my laptop don't like something or Ubuntu don't.

---

### Post by Arukas on 2009-01-05
I am still having my networking problem and I have no clue what to do.

---

### Post by Loosewheel on 2009-01-05
> **Arukas said:**
> I am still having my networking problem and I have no clue what to do.

Did you edit '/etc/network/interfaces'? Try adding these lines.

auto eth0
iface eth0 inet dhcp

And then reboot to see if it works.

---

### Post by Arukas on 2009-01-06
What do you mean by add? Do I just add them below the ones that are there? or do I delete the lines that are already there?

---

### Post by Loosewheel on 2009-01-06
> **Arukas said:**
> What do you mean by add? Do I just add them below the ones that are there? or do I delete the lines that are already there?

Do not delete what is there. Just open up a console and  type:
sudo nano /etc/network/interfaces
 
Then add these two lines:
auto eth0
iface eth0 inet dhcp

just below what is there. Then reboot and see...

---

### Post by Arukas on 2009-01-06
It didn't work, and now the little network box in the corner does not show up.

---

### Post by Loosewheel on 2009-01-06
> **Arukas said:**
> It didn't work, and now the little network box in the corner does not show up.

Great...Well comment out, or remove those lines and see if you get the nm-applet back. This is what my interfaces file looks like:

auto lo
iface lo inet loopback


#iface eth0 inet ipv4ll


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

You have looked at the file after editing it?

---

### Post by Arukas on 2009-01-06
I changed it back to the oringal and the applet came back.

Then I changed my file to match yours.  It still says "disconnected"

---

### Post by Loosewheel on 2009-01-06
> **Arukas said:**
> I changed it back to the oringal and the applet came back.

Then I changed my file to match yours.  It still says 
"disconnected"

Use your original file. And when you click on nm-applet 'wired Network' is checked? And right click = 'Enable Networking' ?

---

### Post by bukwirm on 2009-01-06
Could you post the /etc/network/interfaces file you are using, and the output of ifconfig ?

---

### Post by Arukas on 2009-01-07
This is what the file looks like now.  Before that it was just the first two lines.

[PHP]

auto lo
iface lo inet loopback


#iface eth0 inet ipv4ll


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp
[/PHP]

My network box is enabled.  (with the check)

and i don't know what you want for the ipconfig

---

### Post by bukwirm on 2009-01-07
1. Simply type "ifconfig" in a terminal and post the output.

2. Try using the following as your */etc/network/interfaces*:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

3. After you replace your interfaces file, type "sudo /etc/init.d/networking restart"

---

### Post by Arukas on 2009-01-08
here's my ifconfig, for some reason i was thinking ipconfig


[PHP]



eth0      Link encap:Ethernet  HWaddr 00:06:5b:bb:57:51  
          inet6 addr: fe80::206:5bff:febb:5751/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16104 (16.1 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:11 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18224 (18.2 KB)  TX bytes:18224 (18.2 KB)
[/PHP]

---

### Post by Arukas on 2009-01-08
okay i made the changes and even restarted my computer and it still didn't work.  Nothing is different.

---

### Post by Loosewheel on 2009-01-08
> **Arukas said:**
> okay i made the changes and even restarted my computer and it still didn't work.  Nothing is different.

Hi Arukas,
I downloaded and installed Ubuntu-8.10.
The network is up, and the interfaces file looks like this:

auto lo
iface lo inet loopback

And that is all it needs.

The output of your 'ifconfig' shows an inet6 addr, (IPv6), but no inet addr, (IPv4). I guess you are not getting an ip address from your dsl router. Are you connected to a dsl modem/router/nat type device? If so try another Ethernet cable. Maybe the one you're using is bad. 

Also, 'sudo dhclient' will run the dhcp client and give you some info. You could post the output....but at the bottom it should list: 'DHCPREQUEST....', 'DHCPPACK....', and'bound to'.

You can also right click on the nm-applett, >Edit Connections, >Auto eth0 (highlite it), >Edit (right pane), >IPv4 tab, and make sure 'Automatic (DHCP)' is selected in the drop down. Try this FIRST. 

Good luck

---

### Post by Arukas on 2009-01-08
I am not using a router, the computer is plugged into the modem.

---

### Post by Arukas on 2009-01-08
Here's the output

[PHP]


Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/22:b2:07:fd:c1:48
Sending on   LPF/pan0/22:b2:07:fd:c1:48
Listening on LPF/eth0/00:06:5b:bb:57:51
Sending on   LPF/eth0/00:06:5b:bb:57:51
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


[/PHP]


I plug directly into the modem and the cable is fine, and automatic DCHP is selected.


I think the problem is Ubuntu don't like the network card for some reason.

---

### Post by Loosewheel on 2009-01-08
> **Arukas said:**
> I am not using a router, the computer is plugged into the modem.

Ok. Did you right click nm-applet and check that last step I suggested? Let me know.  I didn't see the output of dhclient the first time....just the previous post.  What kind of modem is it?

---

### Post by Loosewheel on 2009-01-08
The output of dhclient shows that the card is not using an IPv4 address like 192.168.1.3...it shows:
Listening on LPF/eth0/00:06:5b:bb:57:51
Sending on   LPF/eth0/00:06:5b:bb:57:51

so it is not getting an address from your modem. What kind of modem is it? Did you follow the steps in that last proceedure...

---

### Post by Arukas on 2009-01-09
I did.

also, Its a cable modem.  Also, I'm just unplugging, the modem from the working computer and plugging it into the laptop.  

It starts to detect the cable, and then says network disconntect after the network mointer does it things.  Also, I've restarted my laptop with the cable plugged in.

---

### Post by Arukas on 2009-01-09
I have found some better words to describe what I was trying to say.

I think there are driver issuses, is what I am going for  Ubuntu works perfectly on my desktop.

---

### Post by Loosewheel on 2009-01-09
> **Arukas said:**
> I have found some better words to describe what I was trying to say.

I think there are driver issuses, is what I am going for  Ubuntu works perfectly on my desktop.

Sorry I couldn't help....run out of ideas.
You might try 'nopaic' and/or 'apic=off' options at boot.
Or maybe install an earlier kernel.

---

### Post by Arukas on 2009-01-10
Thanks for your help.  

I still would like to find someone who knows how to get my network card working.

---

