---
title: "[SOLVED] Inspirion 1420N &amp;amp; WICD, unable to obtain ip addy?"
date: 2007-12-27
forum: Dell  Ubuntu Support
---

### Post by trooperchix on 2007-12-27
Alright, I got sick and tired of the old wifi management software that ships with this notebook, and I installed WICD.  For some reason I am unable to obtain an IP address.  I had a heck of a time getting this thing installed (I'm just a baby user, man) but it's there.  WICD does find networks out there, both hidden secure and free wifi, but for whatever reason, it can't obtain an IP address.  I'm sure there is a stupid little radio button somewhere that will make this all work, so if one of you guys could help me, I would greatly appreciate it...  

Thanks.
Eddie  

:guitar:         <------- dood needs a stogie...

---

### Post by walkerk on 2007-12-27
> **trooperchix said:**
> Alright, I got sick and tired of the old wifi management software that ships with this notebook, and I installed WICD.  For some reason I am unable to obtain an IP address.  I had a heck of a time getting this thing installed (I'm just a baby user, man) but it's there.  WICD does find networks out there, both hidden secure and free wifi, but for whatever reason, it can't obtain an IP address.  I'm sure there is a stupid little radio button somewhere that will make this all work, so if one of you guys could help me, I would greatly appreciate it...  

Thanks.
Eddie  

:guitar:         <------- dood needs a stogie...

The network is Hidden? So you select the Network drop down and enter the hidden ESSID?

Have you entered the security passphrase? WPA1/2? Next to your network there is an arrow (> YOUR_ESSID), hit it... Now do the same to (> Advanced Settings)... hit it and fill in your settings.. If you're not supplying a passphrase you won't ever be able to pull and IP.

Also, you might try connecting with a static IP within your routers network (perhaps DHCP isn't enabled)

---

### Post by trooperchix on 2007-12-27
> **walkerk said:**
> The network is Hidden? So you select the Network drop down and enter the hidden ESSID?

Have you entered the security passphrase? WPA1/2? Next to your network there is an arrow (> YOUR_ESSID), hit it... Now do the same to (> Advanced Settings)... hit it and fill in your settings.. If you're not supplying a passphrase you won't ever be able to pull and IP.

Also, you might try connecting with a static IP within your routers network (perhaps DHCP isn't enabled)


I can't get an IP addy either on free unsecured wifi hotspots or secured.  Not even at home where I run my own secured (yes, I did enter the password).  But for the free wifi, there isn't a password.  Something somewhere is off.  Any ideas would be welcome...

---

### Post by trooperchix on 2007-12-27
in terminal i ran:

iwconfig

lo                   no wireless extensions
eth0              no wireless extensions
eth1              unassociated  ESSID: "ethostream"
                     Mode:Managed Frequency=2.437GHz Access Point: 00:14:A5:0D:40:5B
                     Bit Rate: 0 kb/s    TX-Power: 16 dBm
                     Power Management:off    
                     Link Quality: 0  Signal level:0 Noise Level:0
                     Rx invalid nwid:0  Rx Invalid crypt:0  Rx invalid  frag:0
                     Tx excessive retries: 0  Invalid misc: 1871  Missed beacon:0

Don't know if any of the above helps or not, but I saw the command in these help pages.  I'm trying to help myself guys, any help would be lovely...

---

### Post by trooperchix on 2007-12-27
> **walkerk said:**
> The network is Hidden? So you select the Network drop down and enter the hidden ESSID?

Have you entered the security passphrase? WPA1/2? Next to your network there is an arrow (> YOUR_ESSID), hit it... Now do the same to (> Advanced Settings)... hit it and fill in your settings.. If you're not supplying a passphrase you won't ever be able to pull and IP.

Also, you might try connecting with a static IP within your routers network (perhaps DHCP isn't enabled)

Hey, I'm just a baby man...  don't know how to do all that.  I figure it's something so obscenely easy because it's starting to piss me off.  Huge tip it's something stupid.  I seem to figure out the hard stuff...  go figure...  What do you mean by WPA 1/2, etc...  more detail would be lovely...  thanks.

---

