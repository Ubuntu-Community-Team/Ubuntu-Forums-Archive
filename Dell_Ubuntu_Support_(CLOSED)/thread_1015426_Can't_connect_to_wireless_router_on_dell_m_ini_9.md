---
title: "Can't connect to wireless router on dell m ini 9"
date: 2008-12-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Canrius on 2008-12-18
Hi! I'm new to Ubuntu. 
I set-up a router today and can't connect to it with my Dell Mini 9. I wasn't sure if it was a problem with the router so I used another laptop to connect to the router and it worked.

I tried a help topic called: troubleshooting 3.2.1 Device recognition.
It says I should open DEVICE MANAGER (system-Preferences-hardware information). I don't have a HARDWARE INFORMATION tab. How can I locate the DEVICE MANAGER? 
I'm not sure if this will help get my wireless connection going, but it says I should follow the instructions step to step.
PLEASE HELP!

---

### Post by Canrius on 2008-12-18
Is it possible that my Belkin G+ MIMO (model F5D9231-4) does not support UBUNTU?

---

### Post by idr3 on 2008-12-20
> **Canrius said:**
> Hi! I'm new to Ubuntu. 
I set-up a router today and can't connect to it with my Dell Mini 9. I wasn't sure if it was a problem with the router so I used another laptop to connect to the router and it worked.

I tried a help topic called: troubleshooting 3.2.1 Device recognition.
It says I should open DEVICE MANAGER (system-Preferences-hardware information). I don't have a HARDWARE INFORMATION tab. How can I locate the DEVICE MANAGER? 
I'm not sure if this will help get my wireless connection going, but it says I should follow the instructions step to step.
PLEASE HELP!

I set up my Mini 9 and had similar issues when I first was trying to connect to the Internet.  Mine resolved to that I had to disable IPv6.  Here is what I did (note you should know vi or google search 'vi commands'):
[B]
sudo vi /etc/modprobe.d/aliases[/B]
[type in your admin password and hit enter]
This will open the file - now change this line: 
**alias net-pf-10 ipv6**
To:
**alias net-pf-10 off**
then **reboot**.

I opened **Firefox** and disabled IPv6:
In the address bar type **about:config** and hit enter
In the filter text box type: **ipv6**
It should show you one result which is: **network.dns.disableIPv6**
It probably says false now.  You want it to say **true**.
Double click on that network.dns.disableIPv6 line and it will set it to true for you.

I also configured my computer to connect to my router.  After I did all of this - I was able to connect to the Internet.  Hope this helps.

---

### Post by idr3 on 2008-12-20
> **Canrius said:**
> 
It says I should open DEVICE MANAGER (system-Preferences-hardware information). I don't have a HARDWARE INFORMATION tab.

I can't see this on mine, either.  Anyone know of a work around or command line?

---

### Post by armandh on 2008-12-21
be sure the wlan is blocked from using the last 2 channels [11?12?]
these will be re-purposed by the FCC and newer equipment [mini9] does not access them 
I saw this in another thread

---

### Post by armandh on 2008-12-21
.dup post

---

### Post by armandh on 2008-12-21
the FCC will repurposed the last two wireless channels [11, 12?]
and newer equipment will not access those. be sure your wlan is blocked from using 11/12

---

### Post by Hula2Pahoa on 2008-12-24
> **Canrius said:**
> Hi! I'm new to Ubuntu. 
I set-up a router today and can't connect to it with my Dell Mini 9. I wasn't sure if it was a problem with the router so I used another laptop to connect to the router and it worked.

I tried a help topic called: troubleshooting 3.2.1 Device recognition.
It says I should open DEVICE MANAGER (system-Preferences-hardware information). I don't have a HARDWARE INFORMATION tab. How can I locate the DEVICE MANAGER? 
I'm not sure if this will help get my wireless connection going, but it says I should follow the instructions step to step.
PLEASE HELP!

Try SYSTEM/ADMINISTRATION then look for the Hardware testing. I ran that first then tried the network link. It finally found my Linksys router, which also has intuitive software which "finds" new computers. I hope this helps!:)

---

