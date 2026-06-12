---
title: "WMP54G Not Working Plz Help!!"
date: 2009-05-11
forum: General Help
---

### Post by cworkman29729 on 2009-05-11
Hi I Have A WMP54G Installed In My Computer And I Have Ndiswrapper & The ndisgtk Installed And When I Select My Rt2500.INF in ndisgtk It Says "Unable To See If Hardware Is Present"

Then I Click OK And In The Currently Installed Windows Drivers List I see rt2500 Then Under That It Says Hardware Present: Yes

And When I Click On Configure Network I gives Me Error "Could Not Find a Network Configuration tool."

How Do I Fix This?

---

### Post by Peter09 on 2009-05-11
Have you seen this thread?

[http://www.gs1.ubuntuforums.org/showthread.php?t=653179](http://www.gs1.ubuntuforums.org/showthread.php?t=653179)

---

### Post by cworkman29729 on 2009-05-11
Ok The Terminal Window Said rt2500 Driver Installed!

Could You Tell Me 1 More Thing! In Windows XP It My Wifi Card Picks up My Router With SSID NETGEAR Which Is The One I Use But In Ubuntu It Isn't Picking It Up! Why Is This?

---

### Post by Peter09 on 2009-05-11
Can you post the output of the terminal command

```
ifconfig
```

---

### Post by cworkman29729 on 2009-05-11
> **Peter09 said:**
> Can you post the output of the terminal command

```
ifconfig
```

```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:e2:7a:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:f3:d4:91  
          inet6 addr: fe80::20f:66ff:fef3:d491/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120 (120.0 B)  TX bytes:328 (328.0 B)
          Interrupt:20 Memory:fc000000-fc002000 

```

---

### Post by Peter09 on 2009-05-11
Your device is still not active. Assuming you now have the driver-

Did you do 

```
sudo modprobe rt2500
```If not try it.

---

### Post by cworkman29729 on 2009-05-11
> **Peter09 said:**
> Your device is still not active. Assuming you now have the driver-

Did you do 

```
sudo modprobe rt2500
```If not try it.

that command gave me 

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rt2500 not found.

---

### Post by Peter09 on 2009-05-11
Hi,
on a wing and a prayer try

```
sudo modprobe rt2561
```

---

### Post by cworkman29729 on 2009-05-11
> **Peter09 said:**
> Hi,
on a wing and a prayer try

```
sudo modprobe rt2561
```


gave me 

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rt2561 not found.

---

### Post by Peter09 on 2009-05-11
Sorry, this is the scattergun approach

```
sudo modprobe rt61
```or
```
sudo modprobe rt61pci
```

---

### Post by cworkman29729 on 2009-05-11
> **Peter09 said:**
> Sorry, this is the scattergun approach

```
sudo modprobe rt61
```or
```
sudo modprobe rt61pci
```

for "sudo modprobe rt61" Gave Same Error

for "sudo modprobe rt61pci" All It Gave Was

"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."


And The Driver Mame Was Rt2500.INF So Isn't That A Rt2500 Driver?

---

### Post by Peter09 on 2009-05-11
I know its a bit confusing - I am confused as well, however that driver appears to be related to your H/W., and with no error message it appears to be installed.

Can you do an ifconfig again?

---

### Post by cworkman29729 on 2009-05-12
Well I Finally Got It To Pickup And Connect To My Router But It Still isn't Connected To The Internet!

What Could Be Causing It To Not Have a Connection To The Internet?

---

### Post by Peter09 on 2009-05-12
Can you show the output of the command

```
route
```

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> Can you show the output of the command

```
route
```

route Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

---

### Post by Peter09 on 2009-05-12
Try adding your default gateway

> **route add default gw {IP-ADDRESS} {INTERFACE-NAME}** Where,
 
[LIST]
[*]IP-ADDRESS: Specify router IP address
[*]INTERFACE-NAME: Specify interface name such as eth0
[/LIST]


---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> Try adding your default gateway

Still Not Working :(

---

### Post by Peter09 on 2009-05-12
Can you show the output of the route command again.

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> Can you show the output of the route command again.

route Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default 192.168.1.1 0.0.0.0 UG 0 0 0 wlan0

---

### Post by Peter09 on 2009-05-12
Can you show the output of ifconfig

---

### Post by ushills on 2009-05-12
can you ping your router directly. if so you will need to set the dns server manually to connect to internet, add nameserver 192.168.1.1 or similar to /etc/resolv.conf.

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> Can you show the output of ifconfig

Added a SnapShot Of The ifconfig output

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> can you ping your router directly. if so you will need to set the dns server manually to connect to internet, add nameserver 192.168.1.1 or similar to /etc/resolv.conf.


in terminal window i type ping 192.168.1.1 and it gives me

ping: sendmsg: Operation not Permitted

---

### Post by ushills on 2009-05-12
that sounds like a permission issue, try sudo ping 192.168.1.1. Also can you post the output of /etc/network/interfaces.  I have got an RT61 card working before but only manually.

---

### Post by Peter09 on 2009-05-12
I cannot see enough of the output. If you are using two machines then to transfer details do this

```
ifconfig >~/Desktop/ifconfig.txt
```

That will put a file with the output onto your desktop.

---

### Post by ushills on 2009-05-12
Also post the output of sudo lspci.  Both RT61pci and RT2561pci have native drivers in Ubuntu from 8.10.  You should not need to use ndiswrapper and it is better if you dont.  Lspci will confirm the card.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> that sounds like a permission issue, try sudo ping 192.168.1.1. Also can you post the output of /etc/network/interfaces.  I have got an RT61 card working before but only manually.

tried sudo ping 192.168.1.1 and gave same error!

how do i display the out put of /etc/network/interfaces?

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> I cannot see enough of the output. If you are using two machines then to transfer details do this

```
ifconfig >~/Desktop/ifconfig.txt
```That will put a file with the output onto your desktop.

Thanks That Helped Alot! Here's The txt file

---

### Post by Peter09 on 2009-05-12
```
cat /etc/network/interface
```

and to get it to a file

```
cat /etc/network/interfaces > ~/Desktop/filename.txt
```

---

### Post by Peter09 on 2009-05-12
Yes, you have a connection on your wireless lan.

---

### Post by ushills on 2009-05-12
lspci > Desktop/lspci.txt

and

cat /etc/network/interfaces > Desktop/interfaces.txt

---

### Post by ushills on 2009-05-12
if you now have a connection do

sudo iwlist -scan and see if you can see your SSID

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> ```
cat /etc/network/interface
```and to get it to a file

```
cat /etc/network/interfaces > ~/Desktop/filename.txt
```

heres the 2 text files

---

### Post by cworkman29729 on 2009-05-12
I Been Connected To The Router Just Can't Browse The Internet

even hooked up to My Router Via Direct Connect And It Didn't Have Internet Either

---

### Post by Peter09 on 2009-05-12
Sorry, your router must have internet if you are using it to send these messages?

So you can connect to your router but not to the internet from the Ubuntu machine - correct?

Just to confirm, using ping in a terminal gives you an error? Try ```
ping www.google.com
```

---

### Post by ushills on 2009-05-12
in that case your router has no dns server settings and these need to be added. go to [www.opendns.com](www.opendns.com) and make a note of their addresses then add these to /etc/resolve.conf in the form nameserver address. then restart firefox.

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> Sorry, your router must have internet if you are using it to send these messages?

So you can connect to your router but not to the internet from the Ubuntu machine - correct?

Just to confirm, using ping in a terminal gives you an error? Try ```
ping www.google.com
```

yes router has internet

Can Connect To The Router But Not To The Internet From Ubuntu Machine

ping [www.google.com](www.google.com) returns unknown host

---

### Post by cworkman29729 on 2009-05-12
internet worked when i first hooked it up To The Router With Wire for like 10min then i tried setting up internet connection sharing! after that it hasn't worked since? 

Does This Make A Difference Of What Might Be Wrong With it?

---

### Post by Peter09 on 2009-05-12
OK - as suggested this is a DNS problem now. Normally this should be set up by your router.

Before doing this see this bug

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204)

This suggest that to fix your gateway problem you need to -

> Commenting out lines relating to rfc3442 in dhclient.conf fixed the issue as well.

Can you try that and then reboot and see if things work?

Note dhclient.conf is in /etc/dhcp3/ and you will need sudo to edit it.

---

### Post by Peter09 on 2009-05-12
Yep - would have been good to have been told before ..... :(

---

### Post by cworkman29729 on 2009-05-12
> **Peter09 said:**
> OK - as suggested this is a DNS problem now. Normally this should be set up by your router.

Before doing this see this bug

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204)

This suggest that to fix your gateway problem you need to -



Can you try that and then reboot and see if things work?

Note dhclient.conf is in /etc/dhcp3/ and you will need sudo to edit it.

I found 2 Lines in dhclient.conf that had the rfc3442 in them and added a # to the beginning of them but still no internet

---

### Post by ushills on 2009-05-12
Please post the output of /etc/resolv.conf, if it is empty add

nameserver 208.67.222.222
nameserver 208.67.220.220

then restart network with

sudo /etc/init.d/networking restart

---

### Post by Peter09 on 2009-05-12
If you enabled internet sharing and then you lost the connection please check through some of the problems in this thread.

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Please post the output of /etc/resolv.conf, if it is empty add

nameserver 208.67.222.222
nameserver 208.67.220.220

then restart network with

sudo /etc/init.d/networking restart


Here is The /etc/resolv.conf Output

And Still No Internet

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> Here is The /etc/resolv.conf Output

And Still No Internet

Okay, so now what happens if you ping 

```
ping www.google.com
```

and

```
ping 192.168.1.1
```

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, so now what happens if you ping 

```
ping www.google.com
```

terminal window says unknown host [www.google.com]("http://www.google.com")

and for ping 192.168.1.1

says operation not permitted

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> terminal window says unknown host [www.google.com](www.google.com)

okay, if you do

```
ping 192.168.1.1
```

what happens, it looks like you have a dns issue and that the dns is not being resolved correctly, try the above to check the connection to the router is still up.

---

### Post by ushills on 2009-05-12
Strange, what do you get with 

```
sudo iwlist scan
```

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Strange, what do you get with 

```
sudo iwlist scan
```


here is the output text for wlan0

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> here is the output text for wlan0

Okay, for some reason the connection quality to your SSID "NETGEAR" is really poor 9/100.  This may be the cause of your frequent disconnections, can you bring the router closer.

Also I would suggest that you add the dns setting directly into the router as you also appear to be having dns issues.

see here for how-to

[https://www.opendns.com/start/device/netgear](https://www.opendns.com/start/device/netgear)

---

### Post by ushills on 2009-05-12
also try 

```
ping 192.168.0.1
``` as we may have being using the wrong router address.

You should also consider changing the router channel to avoid conflicts with the other adjacent router with a higher signal strength.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, for some reason the connection quality to your SSID "NETGEAR" is really poor 9/100.  This may be the cause of your frequent disconnections, can you bring the router closer.

Also I would suggest that you add the dns setting directly into the router as you also appear to be having dns issues.

see here for how-to

[https://www.opendns.com/start/device/netgear](https://www.opendns.com/start/device/netgear)


dk why its only 9% in Windows XP Its More like 20% or more

and in xp it doesn't ever disconnect

can't bring the router closer b/c its upstairs!

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> dk why its only 9% in Windows XP Its More like 20% or more

and in xp it doesn't ever disconnect

can't bring the router closer b/c its upstairs!

Different methods of reporting, I would be more inclined to believe ubuntu but changing channel on router may improve issues due to collisions between signals also try moving aerial orientation on wireless card and use iwlist scan to check signal.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Different methods of reporting, I would be more inclined to believe ubuntu but changing channel on router may improve issues due to collisions between signals also try moving aerial orientation on wireless card and use iwlist scan to check signal.


now it says 20/100

---

### Post by ushills on 2009-05-12
Okay, now we have established that you can see your router and that signal is probably sufficient.

Your dns server settings are okay in ubuntu but not resolving properly.

Now do the following.

1.  See if you can ping the router with ping 192.168.1.1 or ping 192.168.0.1, and report back

2.  Set the dns settings in your router as per the opendns guide, network manager overwrites /etc/resolv.conf on each start up and change of settings an is anoying.

3.  ping [www.google.com](www.google.com) and report back

If this fails I will explain how to set network settings manually as network-manager has always given me problems with rt61 cards.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, now we have established that you can see your router and that signal is probably sufficient.

Your dns server settings are okay in ubuntu but not resolving properly.

Now do the following.

1.  See if you can ping the router with ping 192.168.1.1 or ping 192.168.0.1, and report back

2.  Set the dns settings in your router as per the opendns guide, network manager overwrites /etc/resolv.conf on each start up and change of settings an is anoying.

3.  ping [www.google.com]("http://www.google.com") and report back

If this fails I will explain how to set network settings manually as network-manager has always given me problems with rt61 cards.

pinging 192.168.1.1 returns operation not permitted

pinging 192.168.0.1 returns network not reachable

setting router dns to ones on the opendns guide resulted in no internet period

pinging [www.google.com](www.google.com) returns unknown host

---

### Post by ushills on 2009-05-12
Okay, can you try disabling encryption on the router and try connecting again,  it appears that you cannot connect to your router although you can scan it.

After you have disabled WPA and if you are able to connect we can re-enable and try to get you securely connected.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, can you try disabling encryption on the router and try connecting again,  it appears that you cannot connect to your router although you can scan it.

After you have disabled WPA and if you are able to connect we can re-enable and try to get you securely connected.

its not only the wifi thats broke direct connect to the router and is Still doesn't work! which doesn't require a password

do you think i should just start over With A Fresh Install Of Ubuntu 9.04?

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> its not only the wifi thats broke direct connect to the router and is Still doesn't work! which doesn't require a password

Using the wired connection add the following to /etc/network/interfaces

```
auto eth0

iface eth0 inet dhcp

```

then restart network

```
sudo /etc/init.d/networking restart
```

then ping 192.168.1.1 or ping 192.168.0.1

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Using the wired connection add the following to /etc/network/interfaces

```
auto eth0

iface eth0 inet dhcp

```then restart network

```
sudo /etc/init.d/networking restart
```then ping 192.168.1.1 or ping 192.168.0.1

im getting command not found? for the auto eth0
and the iface eth0 inet dhcp

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> im getting command not found? for the auto eth0
and the iface eth0 inet dhcp

you need to add those lines to /etc/network/interfaces with

```
sudo gedit /etc/network/interfaces
```


then save the file and restart the network with 

```
sudo /etc/init.d/networking restart
```

---

### Post by cworkman29729 on 2009-05-12
i don't have the pc direct connect with the NETGEAR Router Right Now! Here's My Layout

XP Machine Is Connected Wirelessly To The NETGEAR Router!

Then I Have A Linsys Router Connected To The XP Machine With ICS Turned On

the ubuntu is now connected to the linksys router with via ethernet cable

Still Doesn't Get Internet But When i ping the linksys router with ip 192.168.0.1 (ICS IP For Windows) it Recieves replys!

im tryin to make ubuntu the ICS Server instead of my xp machine b/c it makes it very hard to share files :-p

and the linksys router has internet b/c thats how all the computers on first floor are connected :)

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> i don't have the pc direct connect with the NETGEAR Router Right Now! Here's My Layout

XP Machine Is Connected Wirelessly To The NETGEAR Router!

Then I Have A Linsys Router Connected To The XP Machine With ICS Turned On

the ubuntu is now connected to the linksys router with via ethernet cable

Still Doesn't Get Internet But When i ping the linksys router with ip 192.168.0.1 (ICS IP For Windows) it Recieves replys!

im tryin to make ubuntu the ICS Server instead of my xp machine b/c it makes it very hard to share files :-p


You do not need to do this to connect both machines to the internet or share files.

What are you trying to acheive as I believe you are going about it the wrong way.  You can use a single router to connect both machines to the internet, you can also use the same router to create a home network and share files.  You do not need ICS or the additional router.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> You do not need to do this to connect both machines to the internet or share files.

What are you trying to acheive as I believe you are going about it the wrong way.  You can use a single router to connect both machines to the internet, you can also use the same router to create a home network and share files.  You do not need ICS or the additional router.

The Other Computers Can't Even Pick Up The Signal There Wifi Cards Isn't Powerful enough which is 1 of many reasons i need a router on first floor as well

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> the internet connection is on a different floor and i have 2 routers so i was using 1 machine just to connect to the internet and push internet into the router on the first floor that way first floor and second floor has internet but people on 2nd floor can't access files on computers on the first floor

You can do all of this with just the routers, if I understand you do not want the 2nd floor users to access the 1st floor machines.

Assuming the 1st floor router connected to the internet is working okay, you need to connect the 2nd floor router to this.  To do this change the connection settings on the second floor router to the IP address of the 1FL router (if using cable no user name or password will be required), also set the dns-server to the ip address of the 1fl router.

The 2fl router you will want on a seperate network, i.e if 1fl is 192.168.1.1 and 1fl pc's are in this octet then will want to set the ip address of the 2fl router to something like 192.168.2.1 and set the dhcp on this router to serve addresses in the range 192.168.2.2 - 192.168.2.255.

Then connect each machine on the 2fl to the 2fl router and 1fl machines to the 1fl router.  

Now check all machines can access the internet.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> You can do all of this with just the routers, if I understand you do not want the 2nd floor users to access the 1st floor machines.

Assuming the 1st floor router connected to the internet is working okay, you need to connect the 2nd floor router to this.  To do this change the connection settings on the second floor router to the IP address of the 1FL router (if using cable no user name or password will be required), also set the dns-server to the ip address of the 1fl router.

The 2fl router you will want on a seperate network, i.e if 1fl is 192.168.1.1 and 1fl pc's are in this octet then will want to set the ip address of the 2fl router to something like 192.168.2.1 and set the dhcp on this router to serve addresses in the range 192.168.2.2 - 192.168.2.255.

Then connect each machine on the 2fl to the 2fl router and 1fl machines to the 1fl router.  

Now check all machines can access the internet.

so both routers will communicate wirelessly?

---

### Post by ushills on 2009-05-12
you may want to read these

[http://www.qudon.com/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=31](http://www.qudon.com/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=31)

Do you want to share files across all machines.

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> so both routers will communicate wirelessly?


They cannot communicate wirelessly unless one is a bridge, you will need to physically connect the routers with a single ethernet cable, although both routers can connect pc's wirelessly.

see this [http://www.techimo.com/forum/networking-internet/153143-connecting-two-routers-wirelessly-cables.html](http://www.techimo.com/forum/networking-internet/153143-connecting-two-routers-wirelessly-cables.html)

---

### Post by cworkman29729 on 2009-05-12
Well Here's The Real Reason I Need This Working!!! My Phone Got Turned Off b/c of late Payment!!! And I Can't Afford to pay it well my neighbor went and got internet turned on at her house and said that she would keep it on as long as i gave her the money by the 15th of every month 10days in advance!!! Well She Has My Router At Her House so that i can connect to the internet that i pay for! Well I have A Antenna That I Made That Can Pick Up The Internet But I Don't Wanna Be Tied Down To A Wireless Wifi Antenna With A 100ft cable!!! so i tryin to make 1 pc into a internet server that can connect to my router and then share it with my 2nd router so that i can use my laptop anywhere in my house + I Want To be Able To Share My Files With My 2nd Desktop Which serves as a File Backup Server! and of course i don't want my neighbor accessing my files :-p

srry i didn't say this the first time but i just didn't wanna have to say! "My Phone Got Turned Off For Late Payment"

And that im using my neighbors internet 

:guitar: 

any ways now you see why i need this to work! b/c i don't have access to the router with internet at all times :-p

---

### Post by ushills on 2009-05-12
Okay, I don't believe that you can connect ubuntu to the internet through xp's internet connection sharing, when you think you are pinging the xp ics you are actually pinging the linksys router.  The linksys router can create a home network that you can share files through but this is not connected to the internet.  The netgear is connected to the internet directly.

If the routers can act as a bridge you can connect both the routers wirelessly although this is unlikely, you will need to refer to the manuals for each router you may see something in the configuration settings referring to bridging.  The netgear router will need to be set as an access point and the linksys will need to connect to this wireless network.

Depends on the model if this is available, this guide may help if it is.

[http://forums.anandtech.com/messageview.aspx?catid=36&threadid=1513386&enterthread=y](http://forums.anandtech.com/messageview.aspx?catid=36&threadid=1513386&enterthread=y).

Can you not add another wireless card and aerial to the ubuntu machine and just use the netgear router at your neighbours.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, I don't believe that you can connect ubuntu to the internet through xp's internet connection sharing, when you think you are pinging the xp ics you are actually pinging the linksys router.  The linksys router can create a home network that you can share files through but this is not connected to the internet.  The netgear is connected to the internet directly.

If the routers can act as a bridge you can connect both the routers wirelessly although this is unlikely, you will need to refer to the manuals for each router you may see something in the configuration settings referring to bridging.  The netgear router will need to be set as an access point and the linksys will need to connect to this wireless network.

Depends on the model if this is available, this guide may help if it is.

[http://forums.anandtech.com/messageview.aspx?catid=36&threadid=1513386&enterthread=y](http://forums.anandtech.com/messageview.aspx?catid=36&threadid=1513386&enterthread=y).

Can you not add another wireless card and aerial to the ubuntu machine and just use the netgear router at your neighbours.

the linksys router does have internet! and ubuntu was working on it! and even could Surf The internet for the first 10min :-p

---

### Post by ushills on 2009-05-12
Okay, does this thread help

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> the linksys router does have internet! and ubuntu was working on it! and even could Surf The internet for the first 10min :-p

Where was the linksys router getting it's internet connection from the netgear or the xp machine.

This may also help

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

This is an area unknown to me.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, does this thread help

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

thats the thread i followed b4 my internet screwed up on my ubuntu machine

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Where was the linksys router getting it's internet connection from the netgear or the xp machine.

This may also help

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

This is an area unknown to me.

the linksys router gets its ip from the xp machine thats connected to the netgear router & has Internet Connection Sharing Enabled

---

### Post by ushills on 2009-05-12
Okay, now i understand.

with the setup you have you will either need to keep the XP machine using ICS or setup ubuntu to use ICS as the ubuntu communtity guide.  

Ignoring the internet now, as you have 3 machines can they all ping each other and the linksys router.  What is each ip address and the linksys ip address.  Also list the netgear ip address.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, now i understand.

with the setup you have you will either need to keep the XP machine using ICS or setup ubuntu to use ICS as the ubuntu communtity guide.  

Ignoring the internet now, as you have 3 machines can they all ping each other and the linksys router.  What is each ip address and the linksys ip address.  Also list the netgear ip address.

plz note im not giving my Internet IP Address! For Safety reasons
 
-------------------------------------------------
NetGear IP: 192.168.1.1
--------------------------------------------------
Connected To NetGear Router
-----------------------------------------------------
XP Machine With ICS enable: 192.168.1.7

Ethernet Card Connected To Linksys Router: 192.168.0.1
-----------------------------------------------------


-------------------------------------------------
Linksys IP: 192.168.1.1
--------------------------------------------------
Connected To Linksys Router
-----------------------------------------------------
Laptop IP: 192.168.1.101
Ubuntu IP: 192.168.1.102
-----------------------------------------------------

no the pc's can't ping each other!

which is the reason i need a computer thats purpose is to only push internet into the router

b/c with xp's ICS enabled you cant share files when its connected to a router b/c its connected to the internet port

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> plz note im not giving my Internet IP Address! For Safety reasons
 
-------------------------------------------------
NetGear IP: 192.168.1.1
--------------------------------------------------
Connected To NetGear Router
-----------------------------------------------------
XP Machine With ICS enable: 192.168.1.7

Ethernet Card Connected To Linksys Router: 192.168.0.1
-----------------------------------------------------


-------------------------------------------------
Linksys IP: 192.168.1.1
--------------------------------------------------
Connected To Linksys Router
-----------------------------------------------------
Laptop IP: 192.168.1.101
Ubuntu IP: 192.168.1.102
-----------------------------------------------------


The laptop and ubuntu should be able to ping 192.168.1.1 and each other, do you have ufw or another firewall inplace.

However, both private network are using the same addressing, note how both routers ip's are 192.168.1.1 (this will create DHCP addressing conflicts).

Change the linksys ip address and the laptop and ubuntu machines to another octet i.e 192.168.2.1, 192.168.2.101 and 192.168.2.102.  Make sure that the linksys router allocates these address not the netgear.  This network should now function internally without internet and xp ics.  If this works then enable ics and see if this now works.

Perso

[/QUOTE]

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> The laptop and ubuntu should be able to ping 192.168.1.1 and each other, do you have ufw or another firewall inplace.

However, both private network are using the same addressing, note how both routers ip's are 192.168.1.1 (this will create DHCP addressing conflicts).

Change the linksys ip address and the laptop and ubuntu machines to another octet i.e 192.168.2.1, 192.168.2.101 and 192.168.2.102.  Make sure that the linksys router allocates these address not the netgear.  This network should now function internally without internet and xp ics.  If this works then enable ics and see if this now works.

Perso

[/quote]

Changing The Ip to 192.168.2.1 made the router mess up and it no longer had internet & it couldn't be pinged so i changed it back to 192.168.1.1

The NetGear & linksys they shouldn't conflict b/c there not connected together in Any way! 1 pc is connected to wifi internet and the ethernet port is connected to the Internet Hookup On The linksys!

with linksys ip set to 192.168.1.1

i pinged the following

From Laptop I Pinged Router And Got 4 Reply's

From Laptop I Pinged My Ipod Touch and got 4 reply's!

From Laptop Pinged Ubuntu PC And Got No Replys

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> The NetGear & linksys they shouldn't conflict b/c there not connected together in Any way! 1 pc is connected to wifi internet and the ethernet port is connected to the Internet Hookup On The linksys!
[/QUOTE]

They are connected.  They are both connected to the XP machine, being connected wirelesssly or over cable is irrelevent they are on the same private network.

Can you confirm if this is correct

netgear (192.168.1.1) allocates ip of xp machine (192.168.1.7)

XP machine allocates ip of linksys (192.168.1.1)

Linksys (192.168.1.1) allocates ip's of laptop (192.168.1.101) and ubuntu (192.168.102).  

Which router / machine deals with dns resolution and which allocates ip address.

The reason I asked you to change the ip address of the linksys was that you would lose internet connectivity but be able to check if all the pc's connected to the linksys could ping each other and the linksys router, if this is the case then that element of the network is okay, all you needed to do then was connect the linksys with the revised addressing back to the ics on the xp machine and therefore on to the internet.  This all appears to be a dns issue and cannot be resolved with conflicting ip addresses.  it is similar to google and amazon sharing their ip address and expecting it to work.

---

### Post by cworkman29729 on 2009-05-12
Well It Has Something To Do With Ubuntu and not the network! I Put In The ubuntu cd and started a live session and the internet is working just fine!! can browse the web also

and im getting 4 reply's from the ubuntu pc

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> Well It Has Something To Do With Ubuntu and not the network! I Put In The ubuntu cd and started a live session and the internet is working just fine!! can browse the web also

and im getting 4 reply's from the ubuntu pc

Okay, using the live cd what is the ip address.

Post ipconfig, interfaces, route and resolv.conf as previous.

I assume that you are connected via ethernet.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Okay, using the live cd what is the ip address.

Post ipconfig, interfaces, route and resolv.conf as previous.

I assume that you are connected via ethernet.

quick question how to i make it out put to usb flash drive that inserted?

i tried ifconfig >~/Media/disk/ifconfig.txt

but it didn't work

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> quick question how to i make it out put to usb flash drive that inserted?

i tried ifconfig >~/Media/disk/ifconfig.txt

but it didn't work


ifconfig > /media/disk/ifconfig.txt.

you should also copy your interfaces and resolv.conf file if those work on live cd, as you can copy those to your ubuntu setup.

---

### Post by cworkman29729 on 2009-05-12
output must not work on live cd

Ip address is 192.168.1.102

so here is the outputs

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:e2:7a:7a  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fee2:7a7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1724677 (1.7 MB)  TX bytes:289377 (289.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:f3:d4:91  
          inet6 addr: fe80::20f:66ff:fef3:d491/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90 (90.0 B)  TX bytes:324 (324.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-F3-D4-91-34-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

Interfaces
```

auto lo
iface lo inet loopback
```

resolv.conf
```
# Generated by NetworkManager
domain mshome.net
search mshome.net
nameserver 192.168.0.1
```

---

### Post by ushills on 2009-05-12
> **cworkman29729 said:**
> 

resolv.conf
```
# Generated by NetworkManager
domain mshome.net
search mshome.net
nameserver 192.168.0.1
```


Boot into ubuntu normally and using ethernet cable replace the resolv.conf settings with the above settings.  This should now connect to the internet.

---

### Post by cworkman29729 on 2009-05-12
> **ushills said:**
> Boot into ubuntu normally and using ethernet cable replace the resolv.conf settings with the above settings.  This should now connect to the internet.

Still didn't have internet!!!
Im Just Gonna Reinstall ubuntu and start over FRESH :popcorn: 

b/c it looks like i screwed something up really badly :(

an i think 10min to it working is alot easier than "I Might Not Get It Working" :P

---

### Post by cworkman29729 on 2009-05-12
well after being up almost 24hours working on this I Finally Got It Working :)

Linksys Router is connect to the internet Through Ubuntu pc :guitar:
Thanks For All The Help!!!


Here's Some :popcorn: NJoy! :-p

---

