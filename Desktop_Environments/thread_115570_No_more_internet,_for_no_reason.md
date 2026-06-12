---
title: "No more internet, for no reason"
date: 2006-01-10
forum: Desktop Environments
---

### Post by Ubluntu on 2006-01-10
My sony laptop has been running ubuntu fine, I moved it across the house today and the internet won't work anymore. I didn't change any settings, didn't even shut it down. My i.p. addy was static  when this happened, and I was able to ping it from other computers on the network and ping those machines from this one. I tried setting the i.p. to dynamic and it won't grab and i.p. now.

All other machines in the network or working fine. Internet and DHCP

I've noticed before this problem and now trying to troubleshoot that hitting OK when changing network settings in System > Administration > Networking it takes a really long time to complete and close the Networking window.

I'm pretty good with windows network issues but have not been having much luck with linux or ubuntu network problems. My main problem is I didn't change anything, and nothing happened, so I have no idea what to start with.

Thanks for your time

---

### Post by darth_vector on 2006-01-10
the networking window is buggy; lots of people have trouble with it. you are better of setting things up manually.

---

### Post by greenway on 2006-01-10
Did you check the /etc/network/interfaces file to confirm your NIC still has the right configuration?

Run sudo ifdown eth0(or whatever your NIC's name is) and then run sudo ifup eth0(skjhfhj). Try the last one when on DHCP and post the output.

Is you LAN wired or wireless?

---

### Post by Ubluntu on 2006-01-10
Like a dumb ass I posted that and then went ahead with removing the stuff from the interfaces file that I thought was all garbage.. You guys were right, the Networking window added stupid entries in there and removing them made it work great..

The strange thing is I didn't use the Networking window when this problem happened, all I did was un plug it and plug it into the same network and switch on the other end of the house...

Thanks again

Is there a way to use a wireless network that doesn't have WEP? I turn off SSID broadcast and leave WEP disabled on my network..
OR
How do I setup wireless in the interfaces file, do I just not put anything about WEP?

---

### Post by Ubluntu on 2006-01-10
Its happening again, but the interfaces file hasn't changed.. I dont understand.

Why does it take so long when I hit ok on Network and what else do I look for?

ALLDHCPDISCOVER on eth0 2.255.255.255.255 port 67
no DHCPOFFERS recieved.
no working leases in persistent database - sleeping.
ERROR : temporary failure in resolution
run-parts: /etc/network/if-up.d/ntpdate exited with return code 1

whenever I set an i.p. static in my network i enter 255.255.255.0 for my subnet... is that what the problem is here? how do I make it DHCP on a 255.0 subnet? thanks agin

---

### Post by greenway on 2006-01-10
[QUOTE=Ubluntu]Its happening again, but the interfaces file hasn't changed.. I dont understand.

Why does it take so long when I hit ok on Network and what else do I look for?

ALLDHCPDISCOVER on eth0 2.255.255.255.255 port 67
no DHCPOFFERS recieved.
no working leases in persistent database - sleeping.
ERROR : temporary failure in resolution
run-parts: /etc/network/if-up.d/ntpdate exited with return code 1

whenever I set an i.p. static in my network i enter 255.255.255.0 for my subnet... is that what the problem is here? how do I make it DHCP on a 255.0 subnet? thanks agin[/QUOTE]

Hmmmz, strange issue here...

Could it be that perhaps there are two hosts using the same ip address on the LAN?

Usually for small home and office networks a netmask of 255.255.255.0 is used, pretty sure this is the same in your situation so this shouldn't be the problem.

Are you sure you have a DHCP server up and running on your LAN? Is it handing out the right DNS configuration?

---

