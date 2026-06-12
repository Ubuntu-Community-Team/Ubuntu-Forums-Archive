---
title: "Internet Connection on VM"
date: 2006-06-24
forum: Desktop Environments
---

### Post by tomturtle18 on 2006-06-24
I'm running Ubuntu on a VMware virtual machine on top of Windows XP. When I load Ubuntu off of the live CD my internet works just fine, but when I load it in the machine it says server not found. I am using NAT as my network type in the VM. I went into System > Administration > Networking and set my IP address, subnet mask and gateway address and when I try to load a page it just says looking for whatever.com and never loads up. In System > Administration > Network Tools, by default my network device is set to Loopback Interface.

If anyone can help me it's very appreciated. I want to start using ubuntu as my primary OS.

---

### Post by Thund3rstruck on 2006-06-24
I know this doesn't help but I have never gotten any of the networking in VMWare to work correctly except the "bridged networking" which is where your guest OS acts as a seperate machine and pulls a new IP from your router.

---

### Post by tomturtle18 on 2006-06-25
I created a new machine for ubuntu and i used the bridge for my network connection. I ran the liveCD and I still couldn't connect to the internet. I have a built in firewall in my router, and I'm running ZoneAlarm on my host.

---

### Post by darkpark on 2006-06-25
try disabling zonealarm temporarily and see if you can get internet access working in ubuntu.  it's likely that zone alarm is blocking internet access to your vmware machine.   anyway, you'll need to configure zone alarm so that it allows access from your vmware/ubuntu.  you might also want to open the program/application access within zone alarm and see if vmware is listed.  if so, allow it access.

---

