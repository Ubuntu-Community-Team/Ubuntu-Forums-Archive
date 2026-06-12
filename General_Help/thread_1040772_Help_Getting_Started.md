---
title: "Help Getting Started"
date: 2009-01-15
forum: General Help
---

### Post by SkunkFunk on 2009-01-15
Hey all, great community here. I am a rank Linux noob, and trying to bring up my first Ubuntu server to operating capacity. I installed it on an machine that was running W2K SBS that I took out of commission a while back. I am certain that all of the hardware on it is in working order. Right off the bat, the NIC doesnt work. Its a Linksys LNE100TX, which by all accounts should work in Linux by default, but mine does not. ifconfig shows that the static IP i gave it during setup stayed, but im not sure if that means it sees the card. i cannot ping anything. Im trying to move ethtool over to it via flash drive but cannot make that happen either. If i use /dev/sda1 to mount the flash drive I get Access Denied, and trying to use Sudo for that doesn't work at all. Can someone get me started? Thanks!

SkunkFunk

---

### Post by bhaverkamp on 2009-01-15
With your flash stick plugged in please run 'fdisk -l' to list the drive and partitions seen on your system. sda is unlikely to be your flash stick and most likely to be your boot device. You don't really want to be dinking with that unless you know for sure.

---

### Post by spiderbatdad on 2009-01-15
could you post some more info?
```
lspci | grep net
cat /etc/network/interfaces
```

---

### Post by cariboo on 2009-01-15
Also at the prompt:

```
sudo lshw -C network
```

The above command will tell you if the NIC is claimed and the driver loaded. To set a static ip address on the server, if you are running 8.10, remove the dhcp client, so it doesn't go looking for an ip address:

```
sudo apt-get purge dhcp3-client
```

Jim

---

### Post by SkunkFunk on 2009-01-16
> **spiderbatdad said:**
> could you post some more info?


Hi Spiderbatdad, thanks.. Apparently it can see the NIC, but for some reason i cant ping anything on my LAN. here is what I got...

lspci |grep net
02:04.0 ethernet controller: lite-on communications inc LNE100TX {linksys etherfast 10/100} (rev 25)

$ cat /etc/network/interfaces

auto eth0
iface eth0 inet static line address 10.5.5.9
netmask 255.255.255.0
network 10.5.5.0
broadcast 10.5.5.255
gateway 10.5.5.1
# DNS-* options are implemented by the resolvconf package, if installed
dns-nameservers 10.5.5.1
dns-search SF.local


BHAVERCAMP- thx for the info..  You are correct sda1 is the boot device. With the flash drive in i see a device called sdb1.

---

