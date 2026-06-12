---
title: "Uninstalled DHCP, unable to boot into ubuntu 6.06"
date: 2006-09-20
forum: Desktop Environments
---

### Post by ravisghosh on 2006-09-20
Hi

While cleaning up unwanted packages, I uninstalled DHCP thinking I do not need it since I use an dedicated connection with IP that looks like 192.168.1.5 (seems static??) along with some other packages. Now, when I boot ubuntu even in rescue mode, it shows lot of "device-mapper: dm-linear: device lookup failed" lines and then it stops at "configuring network interface." I guess it is because of DHCP being uninstalled only. Also, of note is the fact that I configured kernel from kernel.org and after that it was working fine only without iptables and splash. I have live cd (not alternate cd) and dont know how to recover things. Is there a way I can boot using live cd, mount my / partition, and install dhcp.

Thanks in advance.

Ravi S Ghosh
ravisghosh at gmail dot com
PS: I'm kinda newB.

---

### Post by croak77 on 2006-09-20
Yes. If you boot into the live cd, you can mount your Ubuntu /root partition. For example if your /root is /dev/hda2, then open a terminal and type,
```

sudo mkdir /mnt/recovery
sudo mount /dev/hda2 /mnt/recovery
```

That should mount your /root. Next, you can use chroot to enter the /root partition. So from a terminal type,
```
sudo chroot /dev/hda2 /bin/bash
```

Now you should be all set. Just do sudo apt-get install dhcp. You might want to do a sudo apt-get upgrade to make sure you have all needed dependencies. By chrooting, it's like control your Ubuntu system from the live cd. So you can use apt or any other tool from your install but use the internet connection and tools from the live cd.

---

### Post by ravisghosh on 2006-09-20
thanks for the help. However, the problem was something else. Actually, it was not dhcp that was causing problem. dont know why, but after uninstalling some packages my /etc/networks/intefaces was altered and it was looping continuously searching for eth1, eth2, etc, which i do not have. When booting, I did "ctrl + c" to escape "configuring network interfaces" and then logged in and edited /etc/networks/intefaces commenting off other devices which i do not have and left only eth0.

However, on chrooting, apt could not find dhcp in cd (i dont have internet) saying cdrom is not apt-enabled bla, bla... whereas it is installed in live cd when viewing from synaptic.!!!

but well, the problem was solved...

---

