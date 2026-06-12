---
title: "Installing a New NIC"
date: 2006-08-04
forum: Desktop Environments
---

### Post by MasterXandrex on 2006-08-04
Hi All,

I have been using linux for a while now... first redhat, then ubuntu (Hoary), then Gentoo, and now I'm back to Ubuntu.

In all that time, I've never done much with hardware... all software and development, web administration and the like. I've come across a problem and I don't know how to fix it...

My NIC died on me and I've never swapped hardware on a linux box after the install and I have to admit: I don't know where to start.

Please Help Me,

Thanks

UU

Forgot to put down the symptoms... If the NIC is in alone, there is no listing on ifconfig. If it's with the bad NIC, only the bad NIC has a listing. It is listed in lspci.

---

### Post by mdmarmer on 2006-08-04
I assume you removed the old card and installed the new one, and your BIOS sees the new one OK.  What card and chipset is the new one?  If the driver is in Dapper it should find it and use it -- if not, you'll need to find out what driver to use and go from there.

Mike

---

### Post by MasterXandrex on 2006-08-04
They are both (old and new) Linksys LNE100TX's (I bought the new one hoping for a straight swap) but one is a Generation 1 and the New one in a generation 5.

Also, I know I may need to get a driver, but I need to know how to install it.

---

### Post by thingy on 2006-08-04
> 

Forgot to put down the symptoms... If the NIC is in alone, there is no listing on ifconfig. If it's with the bad NIC, only the bad NIC has a listing. It is listed in lspci.



You may need to activate the new NIC.

To activate or deactivate network connections, do the following:

System->Administration->Networking 

Select Network settings+Connections Tab+Ethernet connection 

Activate/Deactivate




jin

---

### Post by MasterXandrex on 2006-08-04
That would be good if I had a GUI... but this is a server and I have no Xserver on it. Terminal Only...

---

### Post by thingy on 2006-08-04
Ok! You need to edit the /etc/network/interfaces file.

To save you the hassle, can you attach that file to your reply and I'll look at it and ask you how you want to set it up...i think it should be a simple matter of swapping eth0 with eth1 in the file

jin

---

### Post by MasterXandrex on 2006-08-04
actually, I looked in that file and there was no listing for eth1 so I made one cloning the old one and it worked for a bit, but after I restarted it's not listed in ifconfig

my file reads this:

# The Loopback
auto lo
iface lo inet loopback

# primary
auto eth0
iface eth0 inet dhcp


# secondary
auto eth1
iface eth1 inet dhcp


also, if I run ifup -a it says

eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1

---

### Post by MasterXandrex on 2006-08-04
lspci reads the devices as follows:

0000:01:02.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:03.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

---

### Post by thingy on 2006-08-04
> 

eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1



Well that bit means that the kernel modules for your network card didn't get loaded...

Ive got a very fuzzy view of whats going on so can you:

1. Attach output of "dmesg" AND "ifconfig -a" in your next reply
2. Inform us what the make/model of the two nics are and what types they are...onboad the motherboard or pci etc.

jin

---

### Post by MasterXandrex on 2006-08-04
Here it is

---

### Post by thingy on 2006-08-04
eth2 ???  <-- in the ifconfiguredout.txt file

Where did that come from? I can see two AMDtek Comet nics which are eth0 and eth1....but I dont see anything in the dmesg about eth2.

can I have the other info I asked about...make and model stuff please

---

### Post by stormblue on 2006-08-05
> **UbuntuUser3859 said:**
> They are both (old and new) Linksys LNE100TX's (I bought the new one hoping for a straight swap) but one is a Generation 1 and the New one in a generation 5.


There is the make and model.

---

