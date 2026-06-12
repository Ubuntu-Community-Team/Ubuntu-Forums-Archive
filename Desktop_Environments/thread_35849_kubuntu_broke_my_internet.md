---
title: "kubuntu broke my internet?"
date: 2005-05-20
forum: Desktop Environments
---

### Post by nulall on 2005-05-20
i'm sorry if this is a stupid post - i just recently installed ubuntu and am a clueless linux noob
anyways, my internet was working fine on eth0 through my linux wrt54g router, but i just today upgraded to the kubuntu package, and now i can't seem to get my internet connection to work at all.
i'm super confused and tried searching and just got cross-eyed.  sorry again if this is a pain.
i'm not sure what specs you guys would need from my system - please just tell me what info you need (and probably tell me how to get it too).

THANKS!

---

### Post by f.prisson on 2005-05-20
The output of ```
ifconfig
``` and ```
route -n
``` would help.

---

### Post by nulall on 2005-05-20
sorry it took me so long - had to type this all in by hand since my kubuntu box won't connect.  i don't think there are any typos.  the "route -n" seems as though it should have more data than the few words it returned to me - is this the problem?


> ifconfig
eth0  Link encap:Ethernet  HWaddr 00:08:A1:09:18:01
         inet6 addr: fe80::208:a1ff:fe09:1801/64 Scope:Link
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:156 errors:5627 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:19839 (19.3 KiB)  TX bytes:0 (0.0b)
         Interrupt:18 Base address:0xe800

lo      Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:8 errors:0 dropped:0 overuns:0 frame:0
         TX packets:8 errors:0 dropped:0 overuns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)


> route -n
Kernel IP routing table
Destination    Gateway        Genmask        Flags  Metric  Ref

---

### Post by phantom on 2005-05-20
ifconfig eth0 up

or

ifup eth0

And you should be online.

---

### Post by nulall on 2005-05-20
thanks for the reply, but it still seems to not be working

i typed in both commands (ifconfig and route -n) again and got the same results, except a few of the "RX" numbers were different in the eth0 part of the ifconfig

 ](*,)

---

### Post by f.prisson on 2005-05-20
Please poste your /etc/network/interfaces so we can see if your device is konfigured. You can also have a look at System -> Management -> Network.

---

### Post by nulall on 2005-05-20
sorry - i'm dumb and confused

in the terminal, when i type "/etc/network/interfaces" it tells me permission denied
but when i try to "sudo" it, it tells me command not found

i opened network tools in the system menu, but i'm not sure what info you need from it

thanks again for all your help and patience guys (i'm pretty well-versed in windows, so i know how easy it is to get annoyed with people who are just clueless)

---

### Post by maspro on 2005-05-20
[QUOTE=nulall]sorry - i'm dumb and confused

in the terminal, when i type "/etc/network/interfaces" it tells me permission denied
but when i try to "sudo" it, it tells me command not found

i opened network tools in the system menu, but i'm not sure what info you need from it

thanks again for all your help and patience guys (i'm pretty well-versed in windows, so i know how easy it is to get annoyed with people who are just clueless)[/QUOTE]

This command should work:

sudo gedit /etc/network/interfaces

---

### Post by f.prisson on 2005-05-20
> i opened network tools in the system menu, but i'm not sure what info you need from it 

I suspect your network device isn't configured. This configuration is written to /etc/network/interfaces. If you post it we can tell you details.

In the network tools, you can configure your network card, I think you never configured an IP for your system so I suppose you use DHCP. In the default ubuntu desktop there is an applet in the gnome-panel which show the status of the connection.

---

### Post by nulall on 2005-05-20
ok! got it! here's what it says:

# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable netwrok interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
     script grp
     map eth0

# The primary network interface
iface eth0 inet dhcp

---

### Post by f.prisson on 2005-05-20
Add a line

```
auto eth0
``` above

iface eth0 inet dhcp

For this session a ```
ifup eth0
``` must work if your router has an aktive DHCP Server running. If it fails try ```
dhclient eth0
``` or ```
pump eth0
``` Check the result with```
ifconfig eth0
```

---

### Post by nulall on 2005-05-21
hmm...well, i think we're getting closer. i tried all of your 

ifup eth0 tells me "ifup:interface eth0 already configured"

dhclient eth0 tells me a lot, but i think the important part is that it says at the end "No DHCPOffers received", "No working leases in persistent database - sleeping"

pump eth0 tells me "command not found"

and the only change i've noticedin the ifconfig (other than some number changes in the RX packets and bytes) is that the txqueuelen was 0 before and now is 1000

rebooted it in hopes that the added "auto eth0" line would fix it, but it's still not working... :(

any more thoughts? i really like this kde environment, but it looks like i might have to switch back to regular ubuntu to get it to work again...

EDIT: removed unnecessary quoting

---

### Post by f.prisson on 2005-05-21
OK, lets see where we are:> dhclient eth0 tells me a lot, but i think the important part is that it says at the end "No DHCPOffers received", "No working leases in persistent database - sleeping"   means that you have no dhcp server on your router running. do you only have one ethernet device in your computer and are you sure that you are physically connected to your router?

you have to configue a static IP adress with ```
ifconfig eth0 x.x.x.x up
``` but I cannot tell you which net you are using. Take the documention of your router and check which IP and network it uses. Than choose an other IP from this subnet for the ifconfig command. I.e. if your router has the 192.168.0.1 take the x.x.x.2 for you. Then you have to set a default route with ```
route add default gw <router ip>
``` and your internet should work.

Go with any browser on your router and check whether the DHCP Server is enabled.

Don't give up, I think it'a an easy problem!

---

