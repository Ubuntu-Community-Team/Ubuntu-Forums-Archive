---
title: "&quot;Requesting a network address from the wired newtork...&quot;"
date: 2009-01-22
forum: General Help
---

### Post by merciadriluca on 2009-01-22
Hello everybody,

Since I've installed Ubuntu 8.10, I've noticed that, in 75% of my gnome sessions, the small icon indicating that the connection is established stop moving, and, when I approach the mouse to it, it says "Requesting a network address from the wired newtork...", but I never receive any IP adress from my DHCP server.
I'm behind a firewall-router, but I'm here writing from a laptop, with the same Ubuntu edition, and it works pretty well (I have never this problem)! What can I do? I do need this connection to send reports to some of my teachers, so this connection has always to be established.

Sometimes, it works, and there is no problem (directly, it shows "Wired network connection"). What can I do?

Thanks.

---

### Post by yeats on 2009-01-22
In the terminal, do

```
ifconfig
```

and post the output here.

Can you ping your gateway?

---

### Post by merciadriluca on 2009-01-22
On 2 times, it worked 2 times. I'm now going to reboot.
Here is my "normal" ifconfig:
[B]
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:86:ae:b2  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe86:aeb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3748917 (3.7 MB)  TX bytes:595522 (595.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:80:c8:2f:83:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 

[/B].

---

### Post by merciadriluca on 2009-01-22
As a matter of fact, it now works. I hope it will continues. If it stops working (is has now worked 4 times consecutively), I'll post a message in this topic. I have another problem, which is always present. When Ubuntu launches, I receive 4 times:
[B]
usb 3-2: device descriptor read/64 error -110
[/B], followed by:
[B]
usb 3-2: device not accepting address 8 error -110
[/B]
I've noticed that my computer waits 8 or 9 seconds before launching the boot sequence, since this morning. I had never had this ubuntu message (about the usb 3-2) since this morning too.

After receiving this message, there are some other pieces of information, but I can't read them because it goes too fast. What file do I have to look in, to see the last boot log?

I've got to add that I haven't added a new device to the P.C., and I didn't modify any USB driver.

Thanks!

---

### Post by merciadriluca on 2009-01-24
Here is the output of ```
ifconfig
``` when the connection does not work:
[B]
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:86:ae:b2  
          inet6 addr: fe80::21f:c6ff:fe86:aeb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8248 (8.2 KB)  TX bytes:468 (468.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:80:c8:2f:83:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 

[/B]

Any solution, for the usb problem, or for the eth problem? Thanks!

---

### Post by dcstar on 2009-01-24
> **merciadriluca said:**
> Hello everybody,

Since I've installed Ubuntu 8.10, I've noticed that, in 75% of my gnome sessions, the small icon indicating that the connection is established stop moving, and, when I approach the mouse to it, it says "Requesting a network address from the wired newtork...", but I never receive any IP adress from my DHCP server.
........

You may want to experiment with the network configuration, disable Roaming and change it specifically to DHCP.

---

### Post by merciadriluca on 2009-01-25
That's what I do each time, but it still keeps freezing.

---

### Post by Alterax on 2009-01-25
I'm having to make a couple of assumptions here about your network.

Your PC and laptop share your internet connection through the router, which is supplying the DHCP lease assignments.

As most laptop users use a wireless connection, I suppose you're using it for your laptop connection to the router, whereas the PC is on a wired connection. 

If so, then it may be something that caused me no end of troubleshooting grief before, but a damaged network cable could cause intermittent network connectivity like you're experiencing.  Try running your laptop on the wired connection for a day or two (turn off the wireless for that time period as we're using the laptop to test the cable).  Just note if the problem persists.

If the laptop starts behaving the same way, I'd recommend replacing the network cable (about $10 US).  If the wired connection is clean, then try replacing the network card (about $20 US) in your PC (turn off the existing one in the system BIOS if you do).  Network cards do go out over time, and when they do they can really bog down your network AND your motherboard with bogus transmissions.

If replacing the network card doesn't cut it, then the last logical place to look is at the router.  Take the desktop to a friend's to test it out on their connection.  If it behaves when it's out of the house, then it's your router.

I hope this helps; do keep us posted!

---

### Post by merciadriluca on 2009-01-25
> **Alterax said:**
> As most laptop users use a wireless connection, I suppose you're using it for your laptop connection to the router, whereas the PC is on a wired connection. 
(...)
 Try running your laptop on the wired connection for a day or two (turn off the wireless for that time period as we're using the laptop to test the cable).  Just note if the problem persists.


Hello. Evidently, I had forgotten to precise the way my laptop was connected to the router. It is wire-connected: I don't use any wireless network, even if my router is able to.
Sorry, I thought it was clear, because we are (normally :p) not newbies. ;)

Thanks for your help.

---

### Post by merciadriluca on 2009-02-08
up

---

