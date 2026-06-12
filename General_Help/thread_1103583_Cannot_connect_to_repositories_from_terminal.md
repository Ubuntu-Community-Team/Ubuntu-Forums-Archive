---
title: "Cannot connect to repositories from terminal"
date: 2009-03-22
forum: General Help
---

### Post by millsy_c on 2009-03-22
Hi, I now have an ip and the network is started (see [http://ubuntuforums.org/showthread.php?t=1103529]("http://ubuntuforums.org/showthread.php?t=1103529")).
However, I am unable to connect to and download from the online app repositories from the terminal. I'd do it through the gui but that's what stopped working and I uninstalled it, went to reinstall it but found I was unable to do so.
I am also unable to ping my router. Any ideas? Thanks

---

### Post by joseangelini on 2009-03-22
Can you do ping correctly?

Did you check your

/etc/resolv.conf 

file. Has it the DNS name server set?

---

### Post by millsy_c on 2009-03-22
I just saw that my network settings are wrong, but i can't edit them. I'm currently getting some advice in the thread i linked at the beginning of this one. Thanks heaps :)

---

### Post by joseangelini on 2009-03-23
> **millsy_c said:**
> I just saw that my network settings are wrong, but i can't edit them. I'm currently getting some advice in the thread i linked at the beginning of this one. Thanks heaps :)

To config your net you have to edit the 
/etc/network/interfaces
file

#If you are using DHCP server, it have anything like this

auto eth0
iface eth0 inet dhcp

# if you are using static IP the interfaces file have anything like this 
auto eth0
iface eth0 inet static
address 192.168.1.110
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255


Only in the last case you have to edit the /etc/resolv.conf file
and add the DNS servers

nameserver 10.50.50.130
nameserver 10.50.50.131

you should use your own values.

Good luck

---

