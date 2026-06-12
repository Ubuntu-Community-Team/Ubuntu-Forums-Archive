---
title: "Enabling networking - Static  IP's"
date: 2009-04-14
forum: General Help
---

### Post by mervc on 2009-04-14
I have installed Mythbuntu 8.10 but on the first boot, networking is not enabled.  I am not new to Linux and use the CLI everyday.  The Ubuntu doc's only seem to focus on graphical sys administration.

/etc/network/interfaces  is correct
ifconfig eth0  looks good
sudo ifup eth0  reports
eth0 already configured

Mythbuntu does not seem to have Network Manager installed at least it is not in any of the menus.

So if the system is dhcp enabled how to change to static or how to enable the networking?

A similar question on the mythbuntu forum raised to answers,  maybe here?

Merv

---

### Post by jms1989 on 2009-04-14
Add this to your /etc/network/interfaces file: 

iface eth0 inet static
        address 192.168.2.50
        netmask 255.255.255.0
        gateway 192.168.2.1
auto eth0

Change the ip's to match your setup. Namely gateway and address.

---

### Post by mervc on 2009-04-15
> **jms1989 said:**
> Add this to your /etc/network/interfaces file: 

iface eth0 inet static
        address 192.168.2.50
        netmask 255.255.255.0
        gateway 192.168.2.1
auto eth0

Change the ip's to match your setup. Namely gateway and address.

Thanks for the reply.  I didn't have auto eth0 so I added that, the rest are ok.  Still the network is not enabled, even after a reboot.  Checking my Debian unstable it doesn't use the last line,  but Kubuntu 7.10 does.

I recall disabling Network Manager in the Debian install but Kubuntu; I don't remember.  Networking is fine in both of them. I still think Network Manager is the culprit.
Again thanks

---

### Post by mckenna1977 on 2009-04-15
given the above it sounds like you've set up an ip address on eth0

is that the eth port you're system is listening on

try doing ifconfig -a and see the results - you could be on eth1 or more depending on config

can you ping your gateway?

---

### Post by Yashiro on 2009-04-15
> auto eth0
iface eth0 inet static
address 192.168.2.50
netmask 255.255.255.0
gateway 192.168.2.1

Make sure NetworkManager is uninstalled if you haven't done so already.

If you have no network on initial boot try
> sudo /etc/init.d/networking restart

---

### Post by 3Miro on 2009-04-15
Install WICD, it is a better and more stable network manager. Google it for download instructions (it adds to the repos).

---

### Post by Yashiro on 2009-04-15
But there's really no need to manage anything if you just want a basic IP setup.

---

### Post by jms1989 on 2009-04-16
I forgot to mention, add a nameserver entry in your /etc/resolv.conf file after you disable your network manager.

sudo echo "nameserver 192.168.x.1" > /etc/resolv.conf (or just edit it manually)

The network manager must not be allowed to load a boot-up, otherwise it will overwrite your resolv.conf file everytime you power up. Found out the hard way so I just remove it from all machines with static ips.

---

### Post by kpkeerthi on 2009-04-16
> **mervc said:**
> I have installed Mythbuntu 8.10 but on the first boot, networking is not enabled.  I am not new to Linux and use the CLI everyday.  The Ubuntu doc's only seem to focus on graphical sys administration.

/etc/network/interfaces  is correct
ifconfig eth0  looks good
sudo ifup eth0  reports
eth0 already configured

Mythbuntu does not seem to have Network Manager installed at least it is not in any of the menus.

So if the system is dhcp enabled how to change to static or how to enable the networking?

A similar question on the mythbuntu forum raised to answers,  maybe here?

Merv

I would just leave the DHCP on and configure my router to assign a "fixed" IP to my computer based on MAC address.

---

### Post by KeyserSoze93 on 2009-04-16
my /etc/network/interfaces looks like:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0

auto eth0
iface eth0 inet static
        address 10.0.0.6
        netmask 255.0.0.0
        gateway 10.0.0.2

```

Pretty similar, but you might want to watch the "allow hotplug", a friend's networking didn't work till we figured that needed to go in there.

---

### Post by jms1989 on 2009-04-17
> **KeyserSoze93 said:**
> my /etc/network/interfaces looks like:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0

auto eth0
iface eth0 inet static
        address 10.0.0.6
        netmask 255.0.0.0
        gateway 10.0.0.2

```

Pretty similar, but you might want to watch the "allow hotplug", a friend's networking didn't work till we figured that needed to go in there.

I've never seen the hotplug option before, what is it supposed to do? Allow you to remove your nic if needed?

---

