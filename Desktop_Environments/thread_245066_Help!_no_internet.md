---
title: "Help! no internet"
date: 2006-08-27
forum: Desktop Environments
---

### Post by SpikeyMike on 2006-08-27
Hi

being a linux novice I need some help configuring my ethernet connection, I reinstalled ubuntu but I can't get the internet to work, I had it working before but had to reinstall because of a hardware upgrade.  I have tried using static IP and DHCP both of which should work, when I try to open a webpage when using static IP it takes ages and then says page not found, no network connection available, when I use DHCP it just says straight away that no connection is available.  Also I noticed that when I use DHCP the default network device is blank, when I select eth0 and close network settings when I open it again the default gateway device is blank again, I can't get it to stay on eth0.
Also I noticed when I used terminal and typed sudo gedit /etc/network/interfaces I get the following message:

[I](gedit:9412): GnomeUI - WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

then the file opens and displays the following:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.6
netmask 255.0.0.0
gateway 10.0.0.138

auto eth1
iface eth1 inet dhcp

auto eth2
ifacd eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
[/I]

any help greatly appreciated, this is driving me mad ](*,) ](*,)

---

### Post by RRS on 2006-08-27
what hardware did you upgrade to require the reinstall?

Also what type of connection; DSL, cable, etc? And what modem, router, and NIC?

Post back with this info and it's likely someone with a similar set-up and hardware can help.

---

### Post by SpikeyMike on 2006-08-27
Hi RRS

I installed another hard drive and I couldn't get the system to boot because the drive letters had changed, I tried for ages to edit grub but without success so I decided just to reinstall ubuntu. As for my hardware I have adsl internet with a speedtouch modem and seperate switch connecting to my computer through an ethernet connection, hope this is the right info, let me know if it isn't

Mikey

---

### Post by RRS on 2006-08-27
Is there anything listed in the DNS section of Network Settings?

It should have your modems IP under DNS server with "speedtouch something or other"  as the search domain.

From the info in your first post it looks like your modem's IP is 10.0.0.138 if your unsure.

If there's nothing listed under DNS servers try entering the modems IP and then go back to Connections>Properties and activate eth0 as DHCP to see what happens.

Also you might try opening firefox and typing your modems address in to see if you can access it to check its settings for changes.

Hope this at least gets you headed in the right direction.

---

### Post by SpikeyMike on 2006-08-27
Hi
under the DNS section I had put the dns primary and secondary numbers of my ISP, the search domain is LAN which is the name configured in the modem.  10.0.0.138 is the ip of my modem, I can access it ok from my laptop.  Do I need to enter the IP of my modem under DNS servers if I am using DHCP?

Thanks and regards

Mikey

---

### Post by SpikeyMike on 2006-08-27
I tried accessing the modem from firefox on ubuntu but it didn't work, I can access it ok from my laptop though.

---

### Post by RRS on 2006-08-27
> Do I need to enter the IP of my modem under DNS servers if I am using DHCP?

That's the only one I have in mine and when I entered it, it automatically entered a description/name of my modem in search domains.

When I installed Ubuntu on my other machine the modem was connected and DHCP was configured during the installation with the same entries.

I'm also using a router configuered as a switch with the modem set as a router/DHCP server so our basic setups should be the same. 

I don't have any additional entry's for DNS or search domains, were yours suggested by your ISP? I would think as the gateway device only the modem would need your ISP's  DNS numbers but I could be wrong, I'm with ATTYahoo (formerly SBCYahoo).

Also, if your switch has a configuration page you might try to access it's address to. 

Another test might be to simply ping the modem and see if that's successfull.

I had forgotten about [this guide]("http://ubuntuforums.org/showthread.php?t=87643") earlier but it may also help.

Good Luck, let me know if any of this helped.

---

### Post by SpikeyMike on 2006-08-29
Hi RRS

At the moment I have it set up using static IP, I have left the DNS addresses from my ISP there because I know it was working with those before,  what I noticed tho was that when I tried the lspci | grep Eth command as recommended in the link you mentioned it returned the following:

0000:00:14.0 Bridge: nVidia corporation MCP51 Ethernet Controller (rev a3)
0000:03:09.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0
01b (rev 01)

so it looks as if the NIC isn't being recognised

Also I remembered that there is also a wireless network card in the pc which I am not using, could this be causing problems too do you think?

Thanks in advance

Mikey

---

### Post by SpikeyMike on 2006-08-29
Hi again

actually from my last post I am a bit confused about the output, is  one of the entries my wireless card and the other one the ethernet card?

Mikey

---

### Post by RRS on 2006-08-29
> .......is one of the entries my wireless card and the other one the ethernet card?

Most likely. If you've never installed a drver or tried to configure the wireless card it's probably the one not being recognised.

From the readout I'd be willing to guess the wired card is an "on board". You have a nVdia based motherboard?

An unused device shouldn't cause a problem. Both my computers have the dial-up modems dissabled and one has an ethernet card in addition to the Intell onboard and I only have the card enabled with no problems. They all appear in network settings>connections though.

It might be possible that your install mislabeled the devices and your actually trying to activate the wireless card.

Did you try pinging your router, and if so, with what results? 

Are you running Ubuntu on the laptop too or windows only? Compare the settings between the two (I can't remember where to find them in windows though)

Since a static IP worked before you might also want to check with your ISP to verify your connection type. They usually charge extra for a Static vs Dynamic IP.

Hope at least some of this keeps you on the right track to a solution.

---

### Post by SpikeyMike on 2006-08-30
Hi

Yes the wired card is onboard, the mainboard is Asus/HP with nvidia chipset, according to the HP website the onboard LAN is a 10/100 Marvell 88EC031.  I tried pinging the router but it failed,  I am running windows on my laptop and I can ping it from there, also from the windows system on my main pc, I have a dual boot system with windows and ubuntu on seperate hard drives, windows works fine.  If the install did mislabel the devices can I change that manually?

Thanks again for your help

Mikey

---

