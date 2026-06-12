---
title: "DNS Alias"
date: 2005-05-09
forum: Desktop Environments
---

### Post by eltower on 2005-05-09
hey.

I recently installed the Kubuntu distro, and I managed to install the eagle-usb packages that came with the install CD in order to get my USB ADSL modem to work. Now, i still had to set the DNS servers, so as root I ran the network configuration tool on KDE.
Everything went fine until I had to define the DNS servers. When I click on 'Add...' it opens a small dialog box telling me to write in the DNS server IP. When i click on OK though, an error message appears: 'Warning! Alias must be defined'. 
What on Earth does this mean' Is it a bug? Where can i set the alias or whatever on the KDE network tool?
I need help fast, ive been without inernet at home for too long!
eltower

---

### Post by mindspin on 2005-05-09
try sudo vi /etc/network/interfaces

and edit ipaddress, default gateway, and nameserver address

that's the fun in ubuntu, you can control it like woody/sarge or  whatever debian,

if you don't mind using the shell sometimes........

mindspin

(what about "sudo pppoeconf") this is my "tool" to configure dsl

---

### Post by Gandalf on 2005-05-09
sudo gedit /etc/network/interface
in the thernet card section (like eth0) where you can see the IP address
put inside the section
dns-nameservers FIRST_ONE SECOND_ONE
must be ips

and verify that you have the same nameserver entries in
/etc/resolv.conf

---

### Post by mindspin on 2005-05-09
<qoute>and verify that you have the same nameserver entries in
/etc/resolv.conf </qoute>

Yep, that's a good one......... I've  just forgot

mindspin

---

