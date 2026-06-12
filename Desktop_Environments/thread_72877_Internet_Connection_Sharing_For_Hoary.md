---
title: "Internet Connection Sharing For Hoary"
date: 2005-10-07
forum: Desktop Environments
---

### Post by zerhacke on 2005-10-07
I beleive I asked this question several months ago but didn't get an answer I could use.

Here's the situation.  I have two computers.  The main computer is directly connected to a cable modem.  The main computer has two NICs.  The second computer has just one NIC and runs Windows XP.  They are connected by a crossover cable.

Under Windows XP, I can set up the first NIC on the main machine to be shared by the second computer.  What I need is a step by step guide on how to do the same thing under Ubuntu.  I am relatively comfortable with apt-get and configuring files using gedit.  I am not very good at using command line editors such as vi.

For reference purposes, eth0 is connected to the cable modem and eth1 is connected to the second computer.  eth0 gets its information from DHCP.  eth1 has no configuration at all done to it other than what may or may not have been done to it by the installation process.  Both NICs are known to be supported by Linux.  eth0 is a 3Com 3c905TX and eth1 is a Linksys NC100 which I believe uses the Tulip driver.

If anyone can give me a step by step guide from the ground up on how to accomplish this I would really appreciate it.  Telling me to "look into" XYZ package isn't going to get me done, because I don't know enough about Linux or Ubuntu to know what I'm doing.  Again, a step by step guide is needed.

I searched the HOWTO's on this forum for this information and didn't find it.  Maybe this would be a good addition to the HOWTOs on this site.

---

### Post by rmjokers on 2005-10-07
I havent done this in a while, but I think you just have to add this:

net.ipv4.ip_forward=1

in /etc/sysctl.conf.

After you add this, you can either reboot or run

sudo sysctl -w net.ipv4.ip_forward=1

to have the command take effect immediately.  If your network settings are correct (IP addresses and such), your dual-nic box should begin forwarding traffic from the machines on the local network.  If you want your box to act as a firewall, you need to configure that separately.  Not sure what the correct app is in Ubuntu.

---

### Post by mlomker on 2005-10-07
The easiest thing to do is to download the **firestarter** package in Synaptic.  It will configure things for you by asking some questions the first time that you run it.

---

### Post by zerhacke on 2005-10-07
[QUOTE=rmjokers]to have the command take effect immediately.  If your network settings are correct (IP addresses and such), your dual-nic box should begin forwarding traffic from the machines on the local network.  If you want your box to act as a firewall, you need to configure that separately.  Not sure what the correct app is in Ubuntu.[/QUOTE]
So if I don't care about having a firewall at all, I just do the configuration change you suggested.  I'll do it and report back on my findings.

This of course means I'm going to have to manually configure the second NIC's IP and subnet and what have you.  I'll google that, and if I can't find out how to do it I'll come back with another question.

[QUOTE=mlomker]
The easiest thing to do is to download the firestarter package in Synaptic. It will configure things for you by asking some questions the first time that you run it.[/QUOTE]

I'm assuming Firestarter is a firewall package.  I'm not terribly keen on having a firewall just yet.  My second machine does a lot of strange things with strange ports (Mostly gaming) and so I don't want to have to continually update the firewall rules.  Then again I could just configure it to have no blocked ports.

I'll be back guys.  I would like to give a special thanks to the two of you for assisting me here.  The last time I asked a question on this forum I was brushed off, and the whole deal felt like I was a victim of noob-hating.  Thank you for your kind assistance.  I shall be back shortly after trying both solutions and seeing which fits best.

---

### Post by mlomker on 2005-10-07
> I'm assuming Firestarter is a firewall package.  

It is and it also helps you to configure NAT and forward ports.  The problem with Internet Connection sharing is that you have two options: 1) NAT using a different subnet on your second card, 2) A proxy server pretty much only works for HTTP & FTP.

Firestarter gives you a convenient interface for configuring NAT.  Dealing with **ipchains** from a command-line is not for the faint of heart.  rmjoker's suggestion is just going to enable routing but it won't enable NAT or get you onto the Internet, but I could be wrong.

I'm Cisco certified and all that jazz, so networking is a special interest of mine.

---

### Post by zerhacke on 2005-10-07
Jesus you're fast at replying.

Ok, so using firestarter I can essentially turn my computer into a 50 dollar router I can buy from WalMart, complete with NAT and port forwarding.  After configuring firestarter, do I need to do anything on the second computer such as set up IP, subnet, and gateway by hand, or will all that be set up by firestarter using what I guess would be DHCP?

Oh, and, I'm a network nothing.  I know how to get an IP from DHCP and that's about it.  You're certified, so I'll listen to what you have to say.

---

### Post by zerhacke on 2005-10-07
I have a question again.

I know I'm supposed to install DHCP to enable the DHCP server that Firestarter wishes to use when doing internet connection sharing.  However, while editing the dhcpd.conf file to make this possible, I'm stuck at the option domain-name-servers line.  Do I put in my ISP's DNS servers IP address here or what?

Thanks again.

---

### Post by mlomker on 2005-10-07
> Do I put in my ISP's DNS servers IP address here or what?


That sounds right to me.  I haven't configured firestarter to do exactly what you're doing, but I do use it as a personal firewall.

Being certified doesn't always mean a lot, but I do maintain the firewalls and other gear for my company.

---

### Post by zerhacke on 2005-10-08
Problem.

When I attempt to set Firestarter to use DHCP, it gives me a "unknown error" error and refuses to start.  If I choose either option for DHCP use, use what I have or make a new one, it fails.   However, if I do not enable DHCP, firestarter works.

The second computer can only get webpages by IP address when I do this though.  It's as if DNS is not being used.

I'm suspecting dhcpd.conf to be the culprit.  Here's a copy of it from /etc/dhcpd3/

```
# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
	option routers 192.168.0.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers 68.168.240.2;
	option ip-forwarding off;
	range dynamic-bootp 192.168.0.100 192.168.0.254;
	default-lease-time 21600;
	max-lease-time 43200;
}

```

Any ideas?

---

### Post by mlomker on 2005-10-08
> Any ideas?

Try adding this option, with whatever name you like:

```

option domain-name              "example.com";

```

---

