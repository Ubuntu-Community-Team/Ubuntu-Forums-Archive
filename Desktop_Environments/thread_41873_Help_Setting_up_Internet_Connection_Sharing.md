---
title: "Help Setting up Internet Connection Sharing"
date: 2005-06-15
forum: Desktop Environments
---

### Post by JamesNorris on 2005-06-15
I'm a new user to ubuntu, recently switched from Mandrake. My computer connects to the internet and my girlfriend's PC connects through mine (connected through a cat5 crossover cable) when I was using mandrake, I had graphical wizard that I used to automatically connect to the internet and share my connection with my girlfriend's PC. 
I have two problems, now I'm using ubuntu, I have no wizard and each time I load ubuntu, I have to type

```
eaglectrl -a
eaglectrl -w
sudo startadsl
``` 
it won't connect automatically

and I can't find out how to share my ADSL conection (eth0) over my LAN (eth1) Can anyone help??

P.S. Sorry if this is posted in the wrong place... I figured since all my hardware is installed correctly, it didn't want to go in the networking section.

---

### Post by Knome_fan on 2005-06-15
Hi,
how did you setup up your adsl-connection?

I think using sudo pppoeconf is the normal way in hoary and it should give you an option to start the connectiona automatically on boot up.

About sharing your connection, I think you should be able to do it quite easily using firestarter (you'll have to install it first, of course.)

Hope this helps.

---

### Post by JamesNorris on 2005-06-15
[QUOTE=Knome_fan]Hi,
how did you setup up your adsl-connection?

I think using sudo pppoeconf is the normal way in hoary and it should give you an option to start the connectiona automatically on boot up.

About sharing your connection, I think you should be able to do it quite easily using firestarter (you'll have to install it first, of course.)

Hope this helps.[/QUOTE]

No, I didn't use pppoeconf. My account is pppoa, so I just used the eagle-usb configuration utility. Will pppoeconf work with my pppoa ADSL?

---

### Post by JamesNorris on 2005-06-16
[QUOTE=JamesNorris]No, I didn't use pppoeconf. My account is pppoa, so I just used the eagle-usb configuration utility. Will pppoeconf work with my pppoa ADSL?[/QUOTE]

Ok, looks like it doesn't, lol. does anyone else have any idea, then how to autostart my PPPoA ADSL when I boot up?

---

### Post by Dave_is_sexy on 2005-06-16
Oh me me me! I did that last week. Was hard tho.... will see if i an find the thread

---

### Post by JamesNorris on 2005-06-17
[QUOTE=Dave_is_sexy]Oh me me me! I did that last week. Was hard tho.... will see if i an find the thread[/QUOTE]
 Cool, let me know if you find the thread... My girlfriend is forcing me to go into windows whenever shee needs the internet aswell!!

---

### Post by JamesNorris on 2005-06-17
Ok, I have tried firestarter, but I cant share the connection, because firestarter gives me an error starting the firewall, if I run it from konsole, it says it has been unable to start DHCP. I have installed DHCP, but it still doesn't seem to work...  :???: 

If anyone can give me a quick fix, so I can pacify my girlfriend, it would be much appreciated.

---

### Post by pietro_spina on 2005-06-17
how is the LAN connected to your eth1 NIC? hub, router or crossover cable...


--edit--
Ahh never mind... My allergy medicine is making me blind today... I see you already answered that.. sorry

---

### Post by JamesNorris on 2005-06-18
[QUOTE=pietro_spina]how is the LAN connected to your eth1 NIC? hub, router or crossover cable...


--edit--
Ahh never mind... My allergy medicine is making me blind today... I see you already answered that.. sorry[/QUOTE]
 Yeah, it's just a crossover cable. No router or anything

---

### Post by JamesNorris on 2005-06-19
Bump

---

### Post by cwaldbieser on 2005-06-19
Well, given your setup, it seems that what you want to do is set up your Ubuntu machine to *be* the router in your network.  Firestater will let you do this, but it seems like you are having trouble getting it running.  

I don't know that much about how to correct whatever is wrong with your firestarter configuration.  You could try a different firewall program like shorewall, or maybe Guarddog and Guidedog.

I'm no expert, but you could also just enable IP forwarding on your Ubuntu machine, and have the other machine use it as its default gateway.

```
$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
$ cat /proc/sys/net/ipv4/ip_forward
```

The first line turns on IP forwarding.  The second should display a 1 if IP forwarding was set (0 if not set).

The other computer just needs a default route to your machine (which it probably already has if you have connection sharing enabled when you boot into windows).

Note that the other machine ought to have some sort of firewall in this case, because without a proper firewall on your Ubuntu machine, it will be just like that PC was plugged directly into the Internet.

---

### Post by JamesNorris on 2005-06-19
I tried that, and it returned a "1" but it's still not working. 

Also, I just read my syslog and it says

```
Jun 19 21:14:04 ubuntu dhcpd: Internet Systems Consortium DHCP Server V3.0.1
Jun 19 21:14:04 ubuntu dhcpd: Copyright 2004 Internet Systems Consortium.
Jun 19 21:14:04 ubuntu dhcpd: All rights reserved.
Jun 19 21:14:04 ubuntu dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jun 19 21:14:04 ubuntu dhcpd: Wrote 0 leases to leases file.
Jun 19 21:14:04 ubuntu dhcpd: 
Jun 19 21:14:04 ubuntu dhcpd: No subnet declaration for eth0 (168.192.0.1).
Jun 19 21:14:04 ubuntu dhcpd: ** Ignoring requests on eth0.  If this is not what
Jun 19 21:14:04 ubuntu dhcpd:    you want, please write a subnet declaration
Jun 19 21:14:04 ubuntu dhcpd:    in your dhcpd.conf file for the network segment
Jun 19 21:14:04 ubuntu dhcpd:    to which interface eth0 is attached. **
Jun 19 21:14:04 ubuntu dhcpd: 
Jun 19 21:14:04 ubuntu dhcpd: 
Jun 19 21:14:04 ubuntu dhcpd: Not configured to listen on any interfaces!
``` 
when I tried to start DHCP when the PC started, I guess I have my dhcpd.conf configured incorrectly, but I have no idea what it should say... I guess I should have saved a copy from my mandrake installation before I put ubuntu on top of it!!

Does anyone know wha tI should do?

---

### Post by cwaldbieser on 2005-06-19
Do you have the dhcp3-server package installed from Synaptic?  I would guess that it will probably try to set up your configuration for you.  If it doesn't, I have a sample /etc/dhcpd.conf file from O'Reilly's "Linux Cookbook" that I could give you and you could try tweaking with your settings.

---

### Post by JamesNorris on 2005-06-20
Yeah, I apt-get 'ed DCHP3-server but I must have done something wrong, because DHCP clearly isn't working  :? 

It would be great if you could give me your dhcpd.conf :)

---

### Post by logan2004 on 2005-06-20
subnet 192.192.168.100.0 netmask 255.255.255.0 {
range 192.168.100.10 192.168.100.150;
default-lease-time 600;
max-lease-time 7200
}

save and run

```
 sudo dhcpd eth1 
```

---

### Post by jrev on 2005-06-20
Hi friends,

Isn't there in the unofficial guide any topic on howto start to share our internet connection with another ubuntu PC directly connected through a RJ 45 cable ?

We would appreciate to know what sort of applications are necessary to start building this feature...
and if anybody did configure it yet successfully...
 :|  :| 
I am new to the ethernet and new to ubuntu but I bought a laptop without a serial port to connect my external modem (linux special modem)

so I have no choice but to start learning the network system...

A bit confusing at start isn't it ?

---

### Post by JamesNorris on 2005-06-20
[QUOTE=logan2004]subnet 192.192.168.100.0 netmask 255.255.255.0 {
range 192.168.100.10 192.168.100.150;
default-lease-time 600;
max-lease-time 7200
}

save and run

```
 sudo dhcpd eth1 
```[/QUOTE]


james@ubuntu:~$ sudo dhcpd eth0
sudo: dhcpd: command not found

I used eth0, since eth1 is a symlink (I think) to ppp0 as it only becomes a valid location when ppp0 is active. eth0 is my connection to my girlfriend's PC.

---

### Post by JamesNorris on 2005-06-20
[QUOTE=logan2004]subnet 192.192.168.100.0 netmask 255.255.255.0 {
range 192.168.100.10 192.168.100.150;
default-lease-time 600;
max-lease-time 7200
}

save and run

```
 sudo dhcpd eth1 
```[/QUOTE]


Ok, done. I switched eth1 to eth0 when I did it, though, since eth1 is only present when ppp0 is connected. eth0, on the other hand, is my ethernet adapter connected to my girlfriend's PC.

Here;s what it said to me:
```
Internet Software Consortium DHCP Server 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit http://www.isc.org/dhcp-contrib.html

Listening on LPF/eth0/00:0c:f1:ae:9d:66/192.168.100.0
Sending on   LPF/eth0/00:0c:f1:ae:9d:66/192.168.100.0
Sending on   Socket/fallback/fallback-net
There's already a DHCP server running.

exiting.
```

However, my girlfriend's PC still can't connect. I *think* it's because her PC is set to connect through subnet 255.255.0.0 but i could be wrong, this means little to me. I could do with learning it, but I don't have time at the mo (suggestions on what to read would be nice, though)

---

### Post by cwaldbieser on 2005-06-20
That first line:

```
subnet 192.192.168.100.0 netmask 255.255.255.0 
```
Looks a little odd, because there are 5 numbers in that subnet-- normally, there are just 4.  Is it supposed to be 192.168.100.0?

What kind of OS is the other PC running?

The DHCP config you are using looks like it is for a 192.168.100.0/24 subnet.  It is handing out IP addresses between 192.168.100.10 and 192.168.100.150.

The other PC should just be configured to get it's IP address from DHCP, and all should be well.

Don't know why you got the message that another DHCP server is running, though.  I'd try stopping all the dhcp services running and grepping the process table to make sure it's not still running before you restart.

---

### Post by JamesNorris on 2005-06-21
[QUOTE=cwaldbieser]That first line:

```
subnet 192.192.168.100.0 netmask 255.255.255.0 
```
Looks a little odd, because there are 5 numbers in that subnet-- normally, there are just 4.  Is it supposed to be 192.168.100.0?

What kind of OS is the other PC running?

The DHCP config you are using looks like it is for a 192.168.100.0/24 subnet.  It is handing out IP addresses between 192.168.100.10 and 192.168.100.150.

The other PC should just be configured to get it's IP address from DHCP, and all should be well.

Don't know why you got the message that another DHCP server is running, though.  I'd try stopping all the dhcp services running and grepping the process table to make sure it's not still running before you restart.[/QUOTE]


Yeah, I assumed the 192.192 things wasa  typo. The second PC is running WinXP, everything works fine and dandy when I'm in Windows, and worked fine in Mandrake (provided I told the Windows box to update it's IP address.) So I know it's possible to set up ubuntu to work without having to change any settings on her PC.

---

### Post by jrev on 2005-06-21
Hi all,

There should be only one simple way, basically,  to configure an Internet connection with Ubuntu

I have done the tuto on windows 98 and the chapters heading could be the same :

Title :  How to configure and share an Internet connection on your PC's

1)   Introduction to Internet sharing system and TCP/IP operation

2)  What are the hardware and software prerequisites for the configuration 

3)  First steps with Ubuntu 5.04

4)  Configure your Internet server

5)  Configure the Client PC'S

Why not try and make the same procedure for a basicconfiguration of two PC ?

and add later on annexes for more complex situations  ?

OItherwise the beginner will immediately go back to windows ...

Any comments on this pedagogy ?

Thanks for your help to come to an acceptable Howto on the subject

---

### Post by logan2004 on 2005-06-21
ps axe will show you if dhcpd is running, if it is

```
sudo killall dhcpd
```

then try

```
sudo dhcpd eth1
```

sorry about the typo.

---

### Post by Lunde on 2005-06-21
**Easy solution: **Install FireStarter firewall, which is nice to have anyway... then share the internet connection there. 

Edit > Preference > Firewall > Network Settings > Enable Internet connection sharing

And choose in Local Network connetion device the network you want to share it to.

Edit: set the firewall to start at boot for the sharing to be available

---

### Post by JamesNorris on 2005-06-21
[QUOTE=Lunde]**Easy solution: **Install FireStarter firewall, which is nice to have anyway... then share the internet connection there. 

Edit > Preference > Firewall > Network Settings > Enable Internet connection sharing

And choose in Local Network connetion device the network you want to share it to.

Edit: set the firewall to start at boot for the sharing to be available[/QUOTE]


Yep, done that, but my dhcpd.conf isn't configured correctly and DHCP (which firestarter uses to share the connection won't run)

Thanks for the advice guys, I just need to wait unti I can get back into ubuntu again, my girlfriend is using the internet at the mo...

---

### Post by Lunde on 2005-06-21
[QUOTE=JamesNorris]Yep, done that, but my dhcpd.conf isn't configured correctly and DHCP (which firestarter uses to share the connection won't run)

Thanks for the advice guys, I just need to wait unti I can get back into ubuntu again, my girlfriend is using the internet at the mo...[/QUOTE]

Can you use a static address within the DHCP range? maybe the error is that you have to set up the correct gateway, I had the same problem earlier.

---

### Post by JamesNorris on 2005-06-23
[QUOTE=Lunde]Can you use a static address within the DHCP range? maybe the error is that you have to set up the correct gateway, I had the same problem earlier.[/QUOTE]
 I wil give that a try... Problem now, is that we're moving house and we have to move in with my mom until we can arrange a mortgage, so it might be three months before I can test this all now. I will pop back though, when we've moved again.

---

