---
title: "Kubuntu Wireless Setup"
date: 2005-07-26
forum: Desktop Environments
---

### Post by rshol on 2005-07-26
How do you configure wireless cards in Kubuntu (I'm writing this from Mepis because I can't get wireless to work in Kubuntu).

I installed Kubuntu and it recognizes my Orinoco Classic wireless card.  It works "out of the box" with no ploblem in every distro I have every tried (Red Hat, Fedora, SuSE, Mepis) until Kbuntu. I configure the IP, DNS Servers, and gateway from the Networking section of KControl.  I go to the wireless section of Kcontrol and enter my ess id select the box that says I'm using encryption and enter my WEP key as a hex value.   I  click apply and then try to activate the card.  Since I have run kcontrol from a terminal like sudo kcontrol (somebody needs to explain why using sudo is better/easier than having an active root account), there is a terminal open on my desktop and I get an error message when I click activate.  What gives?  How do I configure my card?

---

### Post by PhilippWollermann on 2005-07-27
Hi,

could you please do a

sudo ifconfig -a

in a terminal and post the output? (To see whether the WLAN card is detected correctly, etc.) We'll sure get wireless LAN working for you. :)

Philipp

---

### Post by guitard00d on 2005-07-29
I can run iwconfig and it shows my Orinoco CS card, and I also did everything that the original poster says they did, and mine won't start up automatically either. The only way I can get mine to start up is to open a terminal and execute the following as root:

iwconfig eth1 essid [my_essid]
dhclient

There's got to be a way to make Kubuntu start up the Orinico card automatically without having to jump through those circus hoops. Besides, there's no way in hell that I will ever get my business partner to accept the fact that he's always going to have to do that in order to make his wireless network card work.

One thing that's a bit odd, when you watch the boot up messages, Kubuntu says "configuring network interfaces" (or something like that) before it even starts the PCMCIA services. So, that explains part of the problem. Doesn't fix it, but it explains it.

---

