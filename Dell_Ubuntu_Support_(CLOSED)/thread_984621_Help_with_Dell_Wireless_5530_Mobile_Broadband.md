---
title: "Help with Dell Wireless 5530 Mobile Broadband"
date: 2008-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ionman on 2008-11-16
I just got a new Dell Latitude E4300 through work and it has a Dell Wireless 5530 Mobile Broadband Card in it. The SIM is activated (AT&T) and works well in Windows Vista, but I can't seem to get it to work in Ubuntu 8.10.

The card is detected and shows up in Network Manager (3 times!?) and I choose the AT&T profile. When I click on the Network Manager icon it shows the list of available networks, and I click AT&T. It sits there and tries to connect for about 10 seconds and them says that it has been disconnected.

Can someone help me out? I have Googled this, and searched these forums, and the few directions out there did not make much sense to me at all. This would be a killer feature if I can get it working. So far, Ubuntu has done pretty well on this machine, and I would love to make it a primary OS on here.

Thanks!

- ionman

---

### Post by avilella on 2009-01-25
Hi,

I took the liberty of creating a launchpad team for the people who own or develop for the Dell Latitude E4200/E4300 laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~e4200-e4300](https://launchpad.net/~e4200-e4300)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~15 users I've identified so far.

Cheers,

Albert.


> **ionman said:**
> I just got a new Dell Latitude E4300 through work and it has a Dell Wireless 5530 Mobile Broadband Card in it. The SIM is activated (AT&T) and works well in Windows Vista, but I can't seem to get it to work in Ubuntu 8.10.

The card is detected and shows up in Network Manager (3 times!?) and I choose the AT&T profile. When I click on the Network Manager icon it shows the list of available networks, and I click AT&T. It sits there and tries to connect for about 10 seconds and them says that it has been disconnected.

Can someone help me out? I have Googled this, and searched these forums, and the few directions out there did not make much sense to me at all. This would be a killer feature if I can get it working. So far, Ubuntu has done pretty well on this machine, and I would love to make it a primary OS on here.

Thanks!

- ionman

---

### Post by vigyani on 2009-03-08
Hi

I had similar problem. I installed gnome-ppp using Add/ Remove. Run it and configure the modem. Configure user name and password (provided by the service provider).
Try connecting (Applications==>Internet==>Gnome-PPP). check if it works.

You may have to:
1. edit /etc/ppp/pap-secrets to add user-name and password.
2. Add the system user to dialout and dip groups, to dial out.

For details check:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

---

### Post by yasir.elsharif on 2010-04-17
I have Dell inspiron 1420, which has a sim card slot under the battery and in the bios page it shows that it has wireless, bluetooth and cellular devices.
Ubuntu has never discovers this device
so has anyone with similar harware has it to work
please help

---

