---
title: "Static IP Problem"
date: 2005-04-28
forum: Desktop Environments
---

### Post by Marcel Firlej on 2005-04-28
Hi

I have Static IP config problem. I am using KControl, and this Network Setting addon is **** (no comment) :D

How to setup network IP's by shell script? Anybody can help?
IP, Netmask, Gateway, DNS1, DNS2 for static, and normal dhcp :|

I was never do this by shell :|

And I must say, Ubuntu is better distro than Kubuntu - Ubuntu Utilities is working, but Kubuntu - nice looking KDE only :( But I like Kubuntu  :-? Little, fast and nice

Abybody can help with shell script? I tried use ifconfig but I can`t understand it :| I am somethink like newbie :(

Thanks a lot
  Marcel

---

### Post by nad on 2005-04-28
Your network interfaces are configured with the file: /etc/network/interfaces . If KControl seems confusing or is not able to configure the settings you wish to change, you may edit this file by hand.

In a terminal window type: man interfaces  for instructions.

---

### Post by az on 2005-04-28
install etherconf or do
sudo dpkg-reconfigure etherconf
if it is already installed.


Actually, you can make use of the gtk interface to package configuration in synaptic (apt)  Search for etherconf and right-click and then configure it.  You should get a nice dialogue box...

---

### Post by jobertel on 2005-04-28
On the Kubuntu live CD in Control Panel I was getting a different problem with static IP setup. Trying to designate our DNS server I was told I needed to type in an alias. Thinking it meant typing in the name and address of the DNS server into the hosts list, I tried that but got the same error when trying to add a DNS server. Eth0 was working because I could ping around our LAN but domain name resolution wouldn't work.

John B.

---

### Post by Marcel Firlej on 2005-04-28
Thanks :-)

---

