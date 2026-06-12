---
title: "cant uninstall"
date: 2009-02-22
forum: General Help
---

### Post by flippers on 2009-02-22
hi
ive tried ubuntu and cant get on the net with it so itll have to go..
when i installes ubuntu i partition the whole hard drive prior to install.
now my vista or xp wont  boot up so i can reinstall windows.
ive  got the proper disks..ive put my dvd drive as first boot in the bios etc still nothing any ideas..
as i want to reinstall windows and reinstall ubuntu as a second operating system..im a bit on the thick side when it comes to ubunto so could you explain easily please.
ive got an acer aspire 5315
cheers flipps

---

### Post by kmac on 2009-02-22
What have you tried to get on the net? With Acers, there's not usually much work to get the OS fully operational. I'd hate to see someone give up so easily...

But on the note of your boot disk, see if the Ubuntu LiveCD (Install CD) will boot, and let me know if it does?

---

### Post by flippers on 2009-02-22
hi
yes the ubuntu cd does boot

---

### Post by kmac on 2009-02-22
Hmm... and the Windows one doesn't? 

(Sorry, I'm a RadioShack employee, so I'm going to do the most annoying troubleshooting but...)

Does the Windows CD boot on another machine?

---

### Post by nothingspecial on 2009-02-22
Boot ubuntu. Type ```
lspci -v
``` in your terminal.

If somewhere near the bottom of the output there is a line like this

```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter 
```

Then follow the wireless instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/AspireOne").

Different model but it will work if the card is the same.

---

### Post by kmac on 2009-02-22
> **nothingspecial said:**
> Boot ubuntu. Type ```
lspci -v
``` in your terminal.

If somewhere near the bottom of the output there is a line like this

```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter 
```

Then follow the wireless instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/AspireOne").

Different model but it will work if the card is the same.

AR242x worked for me out of box with 8.10... That was on the Aspire One ZG5.

---

### Post by nothingspecial on 2009-02-22
Not for me on my Samsung nc10 or on my wife`s aspire one. Untill I used the madwifi drivers.

---

### Post by kmac on 2009-02-22
Yeah I had to use madwifi for 8.04 and also use modprobe to disable pin13 on the wireless switch.

At any rate... any word back as to whether or not that disk boots on another machine? I'm not religious or anything, but you might want to consider the idea that this might be a sign from God that Linux shall remain on your computer.

"Though shalt not have any other boot partitions before me."

---

