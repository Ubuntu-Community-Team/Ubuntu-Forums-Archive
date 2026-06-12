---
title: "In case my computer gets stolen"
date: 2006-08-23
forum: Desktop Environments
---

### Post by lonelypauly on 2006-08-23
Are there any programs available for Linux that will report an IP address to a server/email address periodically, in case my computer gets stolen?  I've heard of services for windows notebooks...but what about Linux?

---

### Post by habakkuk on 2006-08-23
Hi Pauly,

If your computer is stolen and subsequently connected to an ISP, it is most likely (always) that a new IP address will be allocated by the thief's ISP. This is because ISPs usually allocate an IP address dynamically - that is, you get a new IP address each time your modem connects; invisible to the user, but convenient for the provider. This would not be helpful for you to recover your computer.

What you could be after is a background utility, that always runs on initial connection to the Internet, that causes some sort of message to be sent to you (or some fixed IP address) giving details of the current IP address and ISP.

If anyone knows of such a utility, please advise. Or how about rising to the challenge ...

This is a great idea that *lonelypauly* raises - OTUG

---

### Post by FuriousLettuce on 2006-08-23
If you had a webserver running, couldn't you write a script to connect to a remote webserver using ssh, login and then upload the current MAC (just in case it is changed), IP and Hostname to the external MySQL server on boot? You could also make it silent if it fails, so that the robber wouldn't know that it was happening?

---

### Post by habakkuk on 2006-08-23
Presumably, if a robber (or subsequent black-market purchaser) connects via an ISP, then s/he could be traced through that provider if the info could be sent.

*Furious* is right; it would have to be in the background/invisible to the user for the villain to be caught.

---

### Post by yopnono on 2006-08-23
> **lonelypauly said:**
> Are there any programs available for Linux that will report an IP address to a server/email address periodically, in case my computer gets stolen?  I've heard of services for windows notebooks...but what about Linux?

And what will that help, when they format and reinstall the machine?
I would say.. that chances are that they reinstall is somewhere around 99%

---

### Post by peabody on 2006-08-23
To my knowledge, you can put any kind of executable script or program into the /etc/networking/if-up.d folder and it will run when your network interface is brought up.

I agree with the previous poster though, this would require that the user actually uses your computer, which isn't likely if they can't get into your account. Also, if you use NetworkManager I don't think this mechanism works.

---

### Post by bluenova on 2006-08-23
> **habakkuk said:**
> Hi Pauly,

If your computer is stolen and subsequently connected to an ISP, it is most likely (always) that a new IP address will be allocated by the thief's ISP. This is because ISPs usually allocate an IP address dynamically - that is, you get a new IP address each time your modem connects; invisible to the user, but convenient for the provider. This would not be helpful for you to recover your computer.

What you could be after is a background utility, that always runs on initial connection to the Internet, that causes some sort of message to be sent to you (or some fixed IP address) giving details of the current IP address and ISP.

If anyone knows of such a utility, please advise. Or how about rising to the challenge ...

This is a great idea that *lonelypauly* raises - OTUG
Actually it would because ISP's have a log of who used what IP at what time.

---

### Post by habakkuk on 2006-08-25
> **bluenova said:**
> Actually it would because ISP's have a log of who used what IP at what time.

But that wouldn't tell the ISP which computer was connected.
There would need to be a way of searching for a MAC address, as this is hard-coded into the hardware. May be difficult though, as this is generally only known to the local router and mapped to its local IP address.

Interrogating all computers for their MAC address may be illegal, and would probably be blocked by firewalls etc.

---

