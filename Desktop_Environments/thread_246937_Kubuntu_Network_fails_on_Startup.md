---
title: "Kubuntu Network fails on Startup"
date: 2006-08-30
forum: Desktop Environments
---

### Post by psadams on 2006-08-30
I have just installed Kubuntu 6.06.1 on my home PC.

About every second time I boot in Kubuntu the networking fails.  I have to go back to the Network Settings toolbox & disable the eth0 interface & then enable it again. This fixes the problem & the networking works again. 

I don't have it networked to another computer. The reason I know the network is failing is because the Internet stops working. It is connected to the router via a LAN cable.

I'm using the onboard LAN on my Epox 9NPA+ ULTRA motherboard (Nvidia Nforce 4 chipset). It is configured to DHCP in the System Settings -> Network Settings toolbox. I have a Billion 7402VGP which handles the DHCP.

Any ideas on what could be causing this problem?

Thanks in advance.

---

### Post by funchords on 2006-08-30
A couple of troubleshooting thoughts...

If there were problems setting up the network device at boot time, it should be reported in **dmesg**.  It's a lot to thumb through, but we don't know at which point it's failing.  

If everything looks good in dmesg, then my thought is that it is not auto-negotiating its speed/parameters properly with the upstream device.  It would be good to compare the output of the command **mii-diag -a** between a boot where the network came up properly and one where it didn't.

---

### Post by Rios on 2006-08-30
Psadams, I have exactly this same problem, so you're not alone.  It's in another thread which is way too far down for me to find.  My problem started when I decided I fancied a look at Kubuntu on my Ubuntu installation.  [-( 

I find that the IP address that I boot up with is unusable, so i have to choose another (either static or DHCP).  Only a reboot with this new address will allow me to use my old one again.

Also found yesterday that it's also affecting the ports I use Amule.  Make sure they're open, Amule reporting they're fully open but an hour or so later Amule reports that they're being firewalled.  Port forwarding is fine on the router, I've now had to install Amule on a Windows laptop which has no problems keeping it open.

---

### Post by psadams on 2006-08-30
> **funchords said:**
> A couple of troubleshooting thoughts...

If there were problems setting up the network device at boot time, it should be reported in **dmesg**.  It's a lot to thumb through, but we don't know at which point it's failing.  

If everything looks good in dmesg, then my thought is that it is not auto-negotiating its speed/parameters properly with the upstream device.  It would be good to compare the output of the command **mii-diag -a** between a boot where the network came up properly and one where it didn't.
Thanks for the advice.

I will have a look at the **dmesg** when I'm home from work today. I'll also look at the output of the command **mii-diag -a** so I can compare it between a sucessful & unsucessful boot. 

The interesting thing is that the past 3 times I've booted the network has worked properly. So, since I posted in this forum, the problem hasn't re-ocurred. :-?

---

