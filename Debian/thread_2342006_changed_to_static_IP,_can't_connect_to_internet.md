---
title: "changed to static IP, can't connect to internet"
date: 2016-11-02
forum: Debian
---

### Post by aeronutt on 2016-11-02
I'm setting up a Debian 8 based file server (first time with such things) on new (cheap) hardware.
I'm mostly using webmin, but some CLI also of course.

After making changes to set a static IP, I can no longer connect to internet, so I messed up or missed something.

Here's my /etc/network/interfaces file:

```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
	address 192.168.0.132
	netmask 255.255.255.0
	network 192.168.0.0
```

Here's my /etc/hosts file:
```
::::::::::::::
/etc/hosts
::::::::::::::
127.0.0.1	localhost
192.168.0.132	servera1 servera1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

I can successfully ping from another computer on the LAN.
Thoughts?

---

### Post by steeldriver on 2016-11-02
What do you mean by "the internet" exactly? The most obvious omission is that you haven't specified any DNS nameserver(s) - so you should be able to connect by IP but not by name. Is that what you're observing?

---

### Post by aeronutt on 2016-11-02
If I 'ping yahoo.com', I get:
```

ping: unknown host yahoo.com

```

If I 'ping 98.138.253.109' (yahoo), I get:
```

connect: Network is unreachable
```

I'm confused about the dns name servers.  webmin (under "Hostname and DNS Client") shows that I have DNS servers as 8.8.8.8.  
But there's nothing in the /etc/network/interfaces file. 

Should there be?

UPDATE: ' more /etc/resolv.conf' shows:
```
::::::::::::::
/etc/resolv.conf
::::::::::::::
nameserver 8.8.8.8
domain hsd1.md.comcast.net.
```

---

### Post by Bucky Ball on 2016-11-03
*Thread moved to **Debian**.*

Can you ping the router/access point? I'm guessing so. Is the router/AP serving IPs via DHCP while you setting a static IP on the local machine? If so, best to set the DHCP server on the router to serve IPs within a range, for instance 192.168.0.100-110, and set the static outside of that range. 

Just a thought ...

---

### Post by aeronutt on 2016-11-03
> **Bucky Ball said:**
> *Thread moved to **Debian**.*

Can you ping the router/access point? I'm guessing so. Is the router/AP serving IPs via DHCP while you setting a static IP on the local machine? If so, best to set the DHCP server on the router to serve IPs within a range, for instance 192.168.0.100-110, and set the static outside of that range. 

Just a thought ...

Thanks for moving this to Debian, I wasn't sure if Debian or Networking was the right place.

Yes, I can ping the router from the server.
I changed the DHCP range on the router to be exclusive of the address of the static server.
No change. Still can't see external addresses from the server.
Thanks for the help so far!  I'm a bit stumped.

---

### Post by Bucky Ball on 2016-11-03
Did you restart both machines after setting the range and static (restart networking)? May be locked on the old IPs. You've probably been there, though ...

---

### Post by aeronutt on 2016-11-03
Ha...yea...I actually just rebooted server and router.
No change.

Not sure what this means, but my router GUI shows only one computer connected to LAN. That is, under the routers 'status' page, it shows "LAN Computers", and it only shows my laptop IP address, and nothing else connected.   Odd, because I can ping the server from the laptop through the router.

---

### Post by Bashing-om on 2016-11-03
aeronutt; Hello;

A thought, often overlooked if a GUI is installed in a server application is network-manager.
Is network-manager installed ?
```

dpkg -l network-manager

```

And if YeS .. who now controls networking ?
You or the system ?
what returns:
```

grep managed= /etc/NetworkManager/NetworkManager.conf

```

[INDENT][INDENT]still maybe this
[INDENT][INDENT][INDENT][INDENT]maybe that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aeronutt on 2016-11-03
Hi Bashing-om, Results:
```
> dpkg -l network-manager
dpkg-query: no packages found matching network-manager
```

And I assume the second command you offered is now meaningless, but:

```
> grep managed= /etc/NetworkManager/NetworkManager.conf
grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory
```

---

### Post by Bashing-om on 2016-11-03
aeronutt; Uh Huh, correct.

Then it is indeed that /etc/network/interfaces file ( you ) control networking.

A name server defined ?
what returns:
```

ls -al /etc/resolv.conf
cat /etc/resolv.conf

```


[INDENT][INDENT]just another thought
[/INDENT][/INDENT]

---

### Post by aeronutt on 2016-11-03
Most excellent help, thanks! Here we go:

```
> ls -al /etc/resolv.conf 
-rw-r--r-- 1 root root 47 Nov  2 21:04 /etc/resolv.conf
```

and

```
> cat /etc/resolv.conf
nameserver 8.8.8.8
domain hsd1.md.comcast.net.
```

Note that "domain hsd1.md.comcast.net." has a 'dot' at the end. Is that a possible issue?

Thanks!

---

### Post by Bashing-om on 2016-11-03
aeronutt; Hey !!


I got my doubts here as:
> 
sysop@1404mini:~$ ls -al /media/sysop/ubie1604//etc/resolv.conf
lrwxrwxrwx 1 root root 29 May 16  2015 /media/sysop/ubie1604//etc/resolv.conf -> ../run/resolvconf/resolv.conf

the config is a symlink to the target " /run/resolvconf/resolv.conf ".
Does the target exist on your system ?
```

ls -al /run/resolvconf/resolv.conf

```

And as this is a static setup .. would it not be better to set DNS in /etc/network/interfaces  ??
see : [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

And yeah I do think that the '.' after net is invalid .. but I also tend to think that even the field "domain" is now invalid in later versions of linux - I could be wrong here ! -. Use of /etc/network/interfaces for DNS will resolve this also .

[INDENT][INDENT][INDENT]maybe now we are seeing some light
[/INDENT][/INDENT][/INDENT]

---

### Post by chili555 on 2016-11-03
Still no DNS and still no gateway...

Please amend your /etc/network/interfaces to:```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
allow-hotplug eth0
iface eth0 inet static
	address 192.168.0.132
	netmask 255.255.255.0
	gateway 192.168.0.1
        dns-nameservers 192.168.0.1 8.8.8.8
```Please verify that the address of the router/gateway is actually 192.168.0.1; you might check the network configuration on other devices on the same network.

Next, do:```
sudo ifdown eth0 && sudo ifup -v eth0
```Did you get the requested address?```
ifconfig
```Can you reach the internet?```
ping -c3 8.8.8.8
ping -c3 www.google.com
```

---

### Post by aeronutt on 2016-11-03
> **Bashing-om said:**
> aeronutt; Hey !!


I got my doubts here as:

the config is a symlink to the target " /run/resolvconf/resolv.conf ".
Does the target exist on your system ?
```

ls -al /run/resolvconf/resolv.conf

```

And as this is a static setup .. would it not be better to set DNS in /etc/network/interfaces  ??
see : [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

And yeah I do think that the '.' after net is invalid .. but I also tend to think that even the field "domain" is now invalid in later versions of linux - I could be wrong here ! -. Use of /etc/network/interfaces for DNS will resolve this also .

[INDENT][INDENT][INDENT]maybe now we are seeing some light
[/INDENT][/INDENT][/INDENT]

Results:
```
> ls -al /run/resolvconf/resolv.conf
ls: cannot access /run/resolvconf/resolv.conf: No such file or directory
```

I had wondered if putting DNS in /etc/network/interfaces was the better way...but I was trying to do everything via webmin, so not quite sure what it's trying to do. Or if I used webmin correctly.

---

### Post by aeronutt on 2016-11-03
UPDATE...SUCCESS!!!!

Adding 
"gateway 192.168.0.1"
"dns-nameservers 192.168.0.1 8.8.8.8"
to /etc/network/interfaces fixed it!

Again, thanks so much for the excellent help, much appreciated, and much to learn!
Thanks.

---

### Post by Bashing-om on 2016-11-03
aeronutt; Outstanding ...

We all do good work here .
Pleased ya got it sorted .

[INDENT][INDENT]I thowt I saw a puddy cat
[/INDENT][/INDENT]

---

