---
title: "Ubuntu and my Xbox"
date: 2005-12-17
forum: General Help
---

### Post by walnut on 2005-12-17
I recently moved from Win2k to Ubuntu and love it but I'm having trouble connecting it to my Xbox.

Part of my trouble might be that I'm using two network cards. I have as Asus A7n8x motherboard that has two ethernet ports on it and I've one port connected to my dsl  and the other connected straight to my Xbox. My internet connection is working perfectly but I can't connect at all to my Xbox. ncftp gives me an "unresolved host" error straight away and ping returns an "operation not permitted" error.

I've my Xbox ethernet connection set to static ip with ip address 192.168.0.1, subnet mask 255.255.255.0 and blank default gateway. I'm running firestarter but I don't think that'd block it. The device is activated and I've restarted my network ```
sudo /etc/init.d/networking restart
```before tring to connect. 

I can't for the life of me think what might be wrong. Anybody got any advice?

---

### Post by iAlta on 2005-12-17
I don't know about Xbox, but Xbox 360 only conncts with Windows xp, I would geuss that Xbox does something like that too.

---

### Post by walnut on 2005-12-17
No. Got my Xbox modded. It's running XBMC.

I had trouble doing it in windows too. If the xbox and broadband were connected at the same time neither of them would work. Don't have a working copy of windows installed at the minute so can't check it again.

---

### Post by BathroomNinja on 2005-12-17
I can ftp into my Xbox just fine.  How do you have your network setup?

This is how mine is:


```


                                        /--------COMPUTER 1 
INTERWEB------>CABLE MODEM--->ROUTER---[---------COMPUTER 2
                                        \--------VOIP BOX
					 \--------XBOX
 

```

Everything has a static IP on my network.   How is your network setup?  You tell me this, and I'm sure I can help you get it working.

---

### Post by walnut on 2005-12-17
It's set up like this:
```

                   xbox
                / 
computer-------
                \
                  router-------------internet

```
Both ethernet ports have static ip addresses.

Hope this is what you're looking for. Thanks for taking the time to help

---

### Post by BathroomNinja on 2005-12-17
OK.  I think the problem is that you have your Xbox connected directly to your computer.  You should have it plugged into your router.  Now, is that a real router or is it actually your cable modem/DSL modem?  Because the modems usually only have 1 output.

You should have it looking something like this...

```


                                        /--------COMPUTER 
INTERWEB------>CABLE MODEM--->ROUTER---[---------XBOX
                                       

```

If you don't have a router, the EASIEST way by far, is to spend $10-20 at Fry's or Walmart to get one.  It will solve this problem and it will work as a Switch, which is a good thing.

---

### Post by walnut on 2005-12-17
It's my DSL modem alright. I'll buy a router if I don't have any joy in the next day or two but I'd prefer to get this working if at all possible. Any ideas?

On a side note. Would a router make it easy for my Xbox to connect to the internet? Wouldn't mind having that option at a later date. Have to get it connecting to my PC first:)

---

### Post by BathroomNinja on 2005-12-17
From what I understand, you have 2 ethernet cards in your computer right?  So, card #1 connects to the DSL router.  Card #2 connects to the Xbox.  You would need to have Card #2 setup to bridge the network so that the Xbox can see the internet.  I'm willing to bet that card #2 is turned off.  I'll be home in a few and I'll help you out more then.

---

### Post by walnut on 2005-12-17
Thanks for all this BathroomNinja. 

You're right about my setup alright. The two ethernet ports came with the motherboard so I figure I might as well make use of them:) 

Card 2 is turned on if I'm understanding you right. Here's the output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:8D:F1:B6
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe8d:f1b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2402355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2284064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1913011142 (1.7 GiB)  TX bytes:324327254 (309.3 MiB)
          Interrupt:22 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:26:54:11:2E:B0
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:54ff:fe11:2eb0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:466 (466.0 b)
          Interrupt:21 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1359026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1359026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200487032 (191.1 MiB)  TX bytes:200487032 (191.1 MiB)

```

Unfortunately I've to head to work soon so I might not be able to reply to you till tomorrow:(

---

### Post by BathroomNinja on 2005-12-17
OK, I found the answer.

Shamelessly stolen from this thread:
[http://ubuntuforums.org/showthread.php?t=66694](http://ubuntuforums.org/showthread.php?t=66694)

It's LOOONG, but I know you can do it.  First off, you need to keep in mind that your internet is on eth0.  This may need to be tweaked some, I don't have 2 ethernet cards so I can't test this out.


```
Creating the network bridge

This section is the hardest section but it brings great rewards. If you want the virtual machine to be accessible by any other computer on the network this section is necessary.

Other wise you can use “user mode” networking and skip to “Section 10 – Qemu-launcher”

Install bridge utilities and user mode utilities

sudo apt-get install bridge
sudo apt-get install uml-utilities

A network bridge is a virtual network interface that contains one or more real/virtual interfaces. Basically what this does is:

Create a bridge device
Add our eth0 (or other LAN device) to the bridge.
Modify security permissions to allow qemu to add a Virtual interface to the bridge.

This will allow your virtual ip address of your virtual pc to have a real ip address on your internal LAN. Get it?

*Note – During this section you will lose network connectivity.
**Note – Please substitute eth0 for the name of your LAN interface.

Create the bridge interface
sudo brctl addbr br0
Give the LAN interface a neutral IP
sudo ifconfig eth0 0.0.0.0
Add the LAN interface to the bridge
sudo brctl addif br0 eth0

Next we have to modify the file /etc/network/interfaces to allow your bridge to obtain an ip address automatically. For static IP, check further below.

sudo vi /etc/network/interfaces

For Dynamic IP

Change these lines from this:

mapping hotplug
script grep
map eth0
To this:

#mapping hotplug
# script grep
# map eth0

From This:
# The primary network interface
iface eth0 inet dhcp

To this:

# The primary network interface
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 1
bridge_hello 1
bridge_stp off

For Static IP

*Note – Substitute all IP addresses in bold for LAN address specific to your setup.

Change these lines from this:

mapping hotplug
script grep
map eth0
To this:

#mapping hotplug
# script grep
# map eth0

From This:

iface eth0 inet static
address 192.168.1.2
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

To This:

auto br0
iface br0 inet static
address 192.168.1.2
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
bridge_ports eth0
bridge_fd 1
bridge_hello 1
bridge_stp off

Now its time to restart the Network and restore network connectivty.

sudo /etc/init.d/hotplug restart
sudo /etc/init.d/network restart

To check if everything went well type ifconfig and check to see if the device br0 listed has an IP address.

Eg

br0 Link encap:Ethernet HWaddr 00:0C:6E:74:41:62
inet addr:192.168.0.77 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::20c:6eff:fe74:4162/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3826802 errors:0 dropped:0 overruns:0 frame:0
TX packets:3899124 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2844083685 (2.6 GiB) TX bytes:3126628692 (2.9 GiB)

Wow you just created a network bridge in linux Good Job!

```

---

### Post by Swab on 2005-12-17
eth0 and eth1 appear to be on different subnets...

---

### Post by BathroomNinja on 2005-12-17
[QUOTE=Swab]eth0 and eth1 appear to be on different subnets...[/QUOTE]

Yeah, you can see that eth0 is getting all of the traffic, so that's obviously on the net.  eth1 is probably waiting for dhcp info and sees nothing so it defaults to what you see there.  If he bridges his connection, then he should be able to get the Xbox online.

---

### Post by walnut on 2005-12-17
Thanks for all your help BathroomNinja.

I'm just about to head out for the night so I won't try it now but I'll give it a go tomorrow and let you know how it goes

---

### Post by BathroomNinja on 2005-12-18
Any luck?

Also, edited to update with this thread:
[http://www.ubuntuforums.org/showthread.php?t=74925](http://www.ubuntuforums.org/showthread.php?t=74925)

It's about setting up a DHCP server on your system.  Might help out.  Also looks a lot easier to follow than the previous thread I linked.

---

### Post by walnut on 2005-12-23
Hey. Sorry. Been a bit of a hectic week.

Didn't have any luck getting it working I'm afraid. Reinstalled widows and it's not working there either.

I have noticed a bit of damage in my network cable however and I'm thinking this might be the problem. I've read through a lot of guides and it shouldn't be as difficult as I'm finding it. I think I might just look into setting up a wireless network as my current configuration is a bit nuts. Got a cable running through the whole lenght of the house:)

---

### Post by BathroomNinja on 2005-12-23
[QUOTE=walnut]Hey. Sorry. Been a bit of a hectic week.

Didn't have any luck getting it working I'm afraid. Reinstalled widows and it's not working there either.

I have noticed a bit of damage in my network cable however and I'm thinking this might be the problem. I've read through a lot of guides and it shouldn't be as difficult as I'm finding it. I think I might just look into setting up a wireless network as my current configuration is a bit nuts. Got a cable running through the whole lenght of the house:)[/QUOTE]


That sucks.  I spent a few days this past summer running CAT5 through my home.  It's never fun to get it setup only to find there is a break in the line.  I still highly recomend getting a cheap wireless router.  It will make it SO much easier and better.

---

### Post by walnut on 2006-01-07
Ok. After a bit of an absence I took your advice and bought a wireless router and wireless ethernet adapter for the Xbox.I just can't seem to get the router to work however. 

I've gone into the "network settings" under the "system" menu and deactivated the port with the router on it, switched the connection to the wireless router, set my ip address to DHCP, reactivated the ethernet port and clicked Okay on "network settings". I can't connect to my router though (or anything else).

Can someone tell me what I'm doing wrong? Don't have much experience with networking in Linux:(

---

### Post by onesojourner on 2006-01-07
do you mean you blocked the port the xbox is on? if you did you don't want it blocked. It needs to be open. you should have the xbox plugged into the router (make sure you don't have a bad cable) make sure you dont have it plugged into the LAN/internet port thats where you plug the dsl modem in. you should be able to log onto the router and see what the IP address of the xbox is.

I have this same set up. XBMC is awesome and if you have a newer build (see pimped edition) its great when its connected to the internet. movie previews and music videos. its awesome.

---

### Post by walnut on 2006-01-07
I'm not following you completely onesojourner. Think you might be a few steps ahead of me. I haven't gotten as far as connecting up the Xbox yet. When I try connecting my wireless router I get stuck straight away. When I try to connect to the router I just get "connection refused" in Firefox. Gotta get this set up before I can tackle the Xbox :) 

Note:All the status led's on the router light up (computer connection, wireless signal, dsl connection) but they don't blink (indicating data being transfered).

---

### Post by jbmalone on 2006-01-07
Do this:

Assuming you have everything set on the router setup.  Turn the computer off, turn the router off from the power cable, and then unplug your modem.  Plug the modem back in and wait until all the lights are back up, and then plug the router back in, and the turn on the computer.  This should reset the modem, which makes it refresh all of the DNS servers and hosts.  If you go into Networking under System, the only DNS server you are probably getting is 192.168.1.1, which is the router and that needs to read the servers your internet works.  

If this doesn't work, post up the model of router and hardware, etc.

---

### Post by walnut on 2006-01-07
I'm using a router and modem in one. It's a "Belkin ADSL Modem with High-Speed Mode Wireless-G Router" (Can't see a model number).[Think this is it.]("http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201522&pcount=&Product_Id=179477")

I presume that it can just take the place of the router/modem I got from my Broadband provider. Am I wrong in this?

---

