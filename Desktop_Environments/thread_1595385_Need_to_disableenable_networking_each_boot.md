---
title: "Need to disable/enable networking each boot"
date: 2010-10-13
forum: Desktop Environments
---

### Post by Wlo on 2010-10-13
Hiya.

I have a strange problem with my networking under Ubuntu.  When I first log in to Gnome both my network adapters are listed as "disconnected" in the network manager applet.  If I right click on the notification icon and disable networking, then wait a few seconds and re enable it, it works fine.

It's happening consistently with Maverick although it seemed only temperamental with Lucid.  I did a fresh Maverick install to see if it would help but it hasn't.

It's the onboard network sockets on a Gigabyte GA-X58A-UD7.  I have two ports but I only use one, it doesn't seem to matter which I use.  It's connected via gigabit ethernet to a Netgear router.  It works fine in Windows 7 (dual boot).

It looks as though something's not quite "ready" when gnome first launches.  The light on the router for the cable is off at first, and only comes on after a few seconds.  It's DHCP.  Same thing happened on the live USB stick (just before the isntaller) and disable/reenable made it work.

Thanks for any help.

Wlo.

---

### Post by bobcollard on 2010-10-13
Right click the Network Icon in the panel and choose "Edit Connections"  Click the Wireless Tab and Edit your Connection.  You may be asked for your password.  Make sure that "Connect Automatically" is checked.  Then "Apply."

---

### Post by Wlo on 2010-10-13
> **bobcollard said:**
> Right click the Network Icon in the panel and choose "Edit Connections"  Click the Wireless Tab and Edit your Connection.  You may be asked for your password.  Make sure that "Connect Automatically" is checked.  Then "Apply."

Hi, thanks for your response.  I'm connected via wired ethernet cable, so the "Wireless" tab is empty, but following your steps for the "Wired" tab, both adapters have the "Connect automatically" ticked.

Any other ideas?

---

### Post by bobcollard on 2010-10-13
> **Wlo said:**
> Hi, thanks for your response.  I'm connected via wired ethernet cable, so the "Wireless" tab is empty, but following your steps for the "Wired" tab, both adapters have the "Connect automatically" ticked.

Any other ideas?
Sorry, no.  If you don't hear anything from another user, Bump your Thread to bring it back to someone's attention.  BTW is your modem on before you startup the computer, or, are they both started at the same time?  The modem itself may be disconnecting when you shut it down.

---

### Post by Wlo on 2010-10-14
> **bobcollard said:**
> BTW is your modem on before you startup the computer, or, are they both started at the same time?  The modem itself may be disconnecting when you shut it down.

Hi.  No the router remains connected to the ADSL line.  There's other devices (NAS drive, printer, PS3, laptop) using it fine whether or not Linux is booted.

Cheers.

---

### Post by bobcollard on 2010-10-14
My question is:  Is the power on to the router and modem all the time?  If you turn it off with the computer, then, it may need to be reset.

---

### Post by Wlo on 2010-10-14
> **bobcollard said:**
> My question is:  Is the power on to the router and modem all the time?  If you turn it off with the computer, then, it may need to be reset.

The router and ADSL router both remain on, and, as I said, all other devices on my network can continue to use them fine, as can Windows on the same machine.

---

### Post by Wlo on 2010-10-18
Not sure if it's related, but when I do enable my network via disable/enable, it's slow, ethtool reports the speed as 10mb/s when I have a gigabit network, card is the onboard for my Gigabyte GA-X58A-UD7.

Full output of ethtool below.  I'm happy to buy a new network card if that may solve it.  Any ideas which one would be likely to work out of the box?

Thanks.

--->
:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

---

### Post by Wlo on 2010-10-21
Fixed it from the instructions in this thread, [http://ubuntuforums.org/showthread.php?t=1480328&page=2](http://ubuntuforums.org/showthread.php?t=1480328&page=2) .

Had to disconnect the power completely and wait as apparently network cards sometimes get themselves in a tiz and they retain their power even whilst PC is off.

Cheers.

---

### Post by mister_p_1998 on 2010-10-21
I got this when I upgraded my mother board from a 10/100 to a gigabyte onboard network card. I finished up plugging in an old network card. What causes it then? and Wont this happen again?
Steve

---

### Post by Wlo on 2010-10-21
> **mister_p_1998 said:**
> I got this when I upgraded my mother board from a 10/100 to a gigabyte onboard network card. I finished up plugging in an old network card. What causes it then? and Wont this happen again?
Steve

I have no idea really if it'll happen again.  I think I first remember it happening after I moved my office around, and had therefore unplugged the machine from the mains.  Sounds like the same for you if it happened after you were doing a hardware upgrade.  I guess it's just something to watch out for after plugging everything back in again.

---

