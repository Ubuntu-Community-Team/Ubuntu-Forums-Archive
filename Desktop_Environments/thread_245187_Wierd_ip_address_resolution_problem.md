---
title: "Wierd ip address resolution problem"
date: 2006-08-27
forum: Desktop Environments
---

### Post by spyke01 on 2006-08-27
For awhile i was off the net and was playing around with "The Perfect Dapper Drake Setup" document, i ended up editing my /etc/network/interfaces and /etc/hosts files. I changed them back later and things were good until this morning after a crash.

Now my box isnt resolving an ip in *nix while winblows is. Whenever i run sudo /etc/init.d/networking restart it goes through the process of releasing the current ip and looks for a dhcp one, the wierd thing is that it recieves a dhcpoffer from an ip I dont recognize. Afterwards, i cant ping out at all and my ip is really funny.

I then replaced my files with an edited version of the live cds files.

My router's ip address: 192.168.100.1

my /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



```

my /etc/hosts file:
```

127.0.0.1 localhost
127.0.1.1 phoenix

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



```

any idea why ts not pulling the correct ip?

---

### Post by Ramses de Norre on 2006-08-27
Could you try commenting out all devices except of lo and the one you're using of /etc/network/interfaces?

And there is something wrong with this line in /etc/hosts I think:
```
127.0.1.1 phoenix
```
Is phoenix your hostname? (your computer's name?), if so the IP on the line should be your machine's internal network IP, I don't know how you define this when you use dhcp but I've got static inet and I've got just my IP on that line.

---

### Post by spyke01 on 2006-08-27
i wouldnt mind doing a static ip of 192.168.100.3, can you post how?

---

### Post by Ramses de Norre on 2006-08-27
Or you use the network-admin dialog, select your device, select static and fill in all the fields.

Or you edit /etc/network/interfaces by hand, mine looks like this:
```
ramses@icarus:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ath0
iface ath0 inet static
        address 192.168.123.106
        netmask 255.255.248.0
        network 192.168.120.0
        broadcast 192.168.127.255
        gateway 192.168.123.254
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid ######
        wireless-key1 ##########
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 195.130.131.1 195.130.130.129

```
This is for a wireless card, but you'll be able to retrieve examples or wired connections on google or the forums.

The first way is the easiest though ;)

---

### Post by spyke01 on 2006-08-27
thanks mate, i tried the gui and it helped some but still had problems, kept working with it and the files and was able to get dhcp back, i will try static again and see what i can get going

thanks for all the help

---

