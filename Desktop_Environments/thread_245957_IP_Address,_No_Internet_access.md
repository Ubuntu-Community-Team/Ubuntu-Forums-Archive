---
title: "IP Address, No Internet access"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Rios on 2006-08-28
Hi, wonder if any kind soul out there can help me please?

I have Ubuntu Dapper, which for the first time for a linux install, does everything I need it to do!

However I have a rather strange problem with accessing the internet.  My PC address is 192.168.1.100 and is static due to port forwarding and QOS from my router.  Everythings fine until I either switch of or reboot.  Upon reboot (which happens uneventfully, no fails) I am unable to access the internet from any application (Firefox, Thunderbird, Gaim).  I am then forced to drop onto DHCP which will allow me to access the internet again.  If I enter my IP address it will still not allow access.  So, leaving the DHCP on, I reboot and then enter the static and everything works again!

And it does this every single time!  I'm presuming it's down to the startup somewhere but I'm pretty new with Linux so don't even know where to start poking about.  ](*,) 

Appreciate any help.

---

### Post by NetworkGuy on 2006-08-28
Sounds like a DNS problem to me.

With DHCP on you get both IP address information as well as DNS information from the DHCP server

When you are using your static IP address, do you go to the DNS tab and verify you have servers listed in there and can ping them?

Let us know.

---

### Post by Rios on 2006-08-28
Sorry I think the DHCP might have been a bit of a red herring.  If I stick in any another static address apart from the 100 one I want to use, it works fine.

Also if I reboot with this new static address it then displays the same problem as the 100 one, although at this point I then change it to 100 and it works... until I reboot again.

Hope that's as clear as mud.

---

### Post by NetworkGuy on 2006-08-28
Yeah, that's mud all right..

Ok, when you can't get to the Internet, are you still able to ping your router and/or any other device behind the router like another PC?   I'm trying to determine if it's your machine or something that might be screwed up with the ARP table of your router.

---

### Post by Rios on 2006-08-28
Yep can ping router and all internal stuff (one laptop and another PC but WinXP).

I've also re-IP'd the laptop with the 100 address, when it's not working on the Ubuntu PC and it works perfectly so I'm reasonably sure (ish!) that it's not the router.

---

