---
title: "Problems connecting with wireless WPC54G"
date: 2008-04-06
forum: Desktop Environments
---

### Post by rashead on 2008-04-06
OK, I finally got the nerve to install Ubuntu on my laptop.  I've got it working great except for one small problem.  I've got a Linksys WPC54G V.3 wireless card which has a Broadcom chipset.  I went through and installed the driver using ndiswrapper and got the card working.  I'm able to go into network configuration and set up the WPA Personal and put in the passcode and the card then connects (In fact I'm using it now).  

When I reboot however, the card is seen, but it doesn't connect to the network.  I then have to remove the card a couple of times and then go back into Network configuration and put in the passcode again.  After doing this, the card then connects once again.  (When going in, I still see that there is information stored there, I just need to put it in again for it to connect)

I've gone in and blacklisted ipv6 because initially the card kept picking up some sort of ipv6 address even though I don't have ipv6 on my network.  So, ipv6 is disabled.  

It's not a terrible problem, but it is kind of a pain.  If anyone has any ideas or has come across this before, let me know.  I really don't want to make things worse though, it was pain enough getting it to the point where it is now.:)

Thanks again

---

### Post by Pnut on 2008-04-06
did you forget to append the driver to startup?

sudo modprobe ndiswrapper

I was using a wpc54g v4 card and had this same problem when i forgot to modprobe the ndiswrapper driver

---

### Post by rashead on 2008-04-06
I think I did the same thing by going in and adding ndiswrapper to the modules file.  I went and tried your suggestion though, and I've got the same problem.

Thanks

---

