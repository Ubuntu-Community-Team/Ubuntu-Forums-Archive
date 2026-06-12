---
title: "ipconfig /release, /renew equivalent"
date: 2006-02-12
forum: Desktop Environments
---

### Post by dantheman on 2006-02-12
Hey, I've been racking my brain about this. My ISP requires me to reset my IP address before getting full access of the internet. I got a new motherboard --> new MAC address and that's why. 

This is very simple in Windows command prompt:
> ipconfig /release
> ipconfig /renew

How do you do this in linux?? I've tried ifconfig options and ip address flush eth0 with no luck. Please help, thanks!

---

### Post by kaamos on 2006-02-12
Assuming your interface is eth0
```
sudo ifdown eth0
sudo ifup eth0
```

Hope this helps.

---

### Post by dantheman on 2006-02-12
I tried:

> sudo /etc/init.d/networking stop
> sudo /etc/init.d/networking start

but that didn't work. 

Yes, my ethernet adapter is "eth0".

---

### Post by Spano on 2006-02-12
to setup the network card then try DHCP manually, do :

> sudo ip addr flush dev eth0 && sudo ip link set eth0 down
> sudo ip link set eth0 up
> sudo /sbin/dhclient eth0

Maybe this?

---

### Post by dantheman on 2006-02-12
my friend says:

> sudo dhclient

any opposition?

---

### Post by 5-HT on 2006-02-12
[quote=dantheman]my friend says:

> sudo dhclient

any opposition?[/quote]
Hi, yup if you are using dhcp for your ip, I've found that I've needed to do: ```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0 
```

This seems to get everything working again.


HTH

*EDIT: my advice seems very similar to that provided by Spano, not really sure why that didn't work, but maybe going through ifconfig would (has for me at least, and is much more forgiving than flushing the protocol addresses if anything goes wrong such as a typo or wrong device).

---

### Post by dantheman on 2006-02-12
thanks guys/girls

there's 10" of snow in Boston and it's only half done :)

---

### Post by Spano on 2006-02-12
Here is the text from an earlier post in this forum, don't have a link, or know the guys name, but it has helped me a lot setting up a static ip and  it might help you with doing what I think your doing.  Good luck!

> Wait don't format.

The networking configuration in Debian/Ubuntu/Kubuntu? is super simple.

there's this one file /etc/network/interfaces

It has a super simple syntax.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

is all you need to get dhcp setup on your first network card. If DHCP doesn't work you can set a static ip by changing the file to :

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.6.4
netmask 255.255.255.0
gateway 192.168.6.1

See I've commented out the dhcp line. When we fix the DHCP server, we can comment out the static sections and put back dhcp.

After changing this file, you can do one of the foll to enable the change:
> sudo /etc/init.d/networking restart
OR
> sudo ifdown eth0 && sudo ifup eth0

Note that the indenting is not important. I just think it looks nice.

If those don't wor, or you want to try something else, you can use the ip command (installed on Ubuntu by default, available in the iproute2 package on Debian).

to de-configure the network card :
> sudo ip addr flush dev eth0
to add an ip address :
> sudo ip addr add 192.168.6.4/24 dev eth0
to setup the network card then try DHCP manually, do :

> sudo ip addr flush dev eth0 && sudo ip link set eth0 down
> sudo ip link set eth0 up
> sudo /sbin/dhclient eth0


I hope this helps your worries.

---

### Post by 5-HT on 2006-02-12
Not sure if this is pertinent, but:
a) Are you going through cable/DSL instead of dialup?
b) Is your ip static or dynamic?
c)Also, is there a router in place (I'm guessing no because that wouldn't block anything to do with your ISP, but if you do have one, you may need to change the router settings to reflect your new MAC if you have MAC filtering enabled)?


If a) and possibly c) are true [b) is just to know if you need to run dhclient], you'd probably need to powercycle the modem/router after changing the MAC and changing the router to allow the new MAC to connect (if applicable).

Best thing (this is overkill but will guarantee to reset everything properly) is to:

I. shut down pc
II. unplug modem & router (if applicable)
III.wait 20 seconds
IV.plug modem back in
V. wait for it to get block sync (until the lights do what they normally do, or just wait 30 seconds)
VI. plug the router back in (if applicable)
VII. wait 30 seconds
VIII. turn on pc

At this point you should be good to go, but if not try another round of my last post or Spano's.

---

