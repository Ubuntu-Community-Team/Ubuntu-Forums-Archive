---
title: "Waiting for network interface to come up..."
date: 2006-01-14
forum: General Help
---

### Post by DarkAngel88 on 2006-01-14
Hi,

I think I just messed everything up with Ubuntu.  I was playing around with kismet and suddently my laptop crashed so I had to restart it manualy (holding the power button...)

But now the problem is that during the loading screen of ubuntu, the system hangs on the "Waiting for network interface to come up" and I get a "fail" after 3-4 minutes of waiting.  When I log in Ubuntu, I get a problem with my wireless card not getting a IP address from the router.  Now is there a way to get everything back to normal without having to reinstall everything ??

If I want to get a IP address, I have to configure it manualy using the "sudo ifconfig ath0 up", then the "sudo iwconfig ath0 essid linksys" and then the "sudo dhclient ath0" else it wont work.

Please someone help me with this issue !

Thanks !

---

### Post by healychan on 2006-01-14
> "Waiting for network interface to come up" and I get a "fail" after 3-4 minutes of waiting.
Press Ctrl + c next time to skip that bit. It saves your time.

> If I want to get a IP address, I have to configure it manualy using the "sudo ifconfig ath0 up", then the "sudo iwconfig ath0 essid linksys" and then the "sudo dhclient ath0" else it wont work.
Check your /etc/network/interfaces file. If you find that a line ```
auto ath0
```is missing, add it back and restart to see if it works.

Before you modify the file, make a backup first.

---

### Post by DarkAngel88 on 2006-01-14
Wow, it worked !!  Thanks !!

While you are here, I got another question regarding this issue.  Is there a way to reduce the timeout time for a network interface to come up ?  I mean, I use my wireless interface 99% of the time and the other 1% is my eth0 interface.  The problem is that when I'm booting Ubuntu, I still have to wait a certain amount of time (~2 min) before I get the "ok" sign. 

I'm pretty sure that it's the eth0 that takes time to come up and it takes time for the system to realize that eth0 won't get a ip address.  

So I think that reducing the amount of time for the system to try to get a IP address from eth0 will help this issue.  I'm a right and if so, is there a way to bypass all this ?

Thanks again healychan !

---

### Post by DarkAngel88 on 2006-01-14
Am I the only one with this problem ??

---

### Post by healychan on 2006-01-14
> 
So I think that reducing the amount of time for the system to try to get a IP address from eth0 will help this issue.  I'm a right and if so, is there a way to bypass all this ?
I was having the same problem.
I disable the interface eth0 by modifying /etc/network/interfaces file.
Check /etc/network/interfaces again, remove```
auto eth0
```.
If still doen't work, remove something like```
iface eth0 inet dhcp
```
I couldn't remember what the whole line looks like, but it start with "iface" and ended with "dhcp". That line determined that the interfaces will try to gain an IP from DCHP server.

> Thanks again healychan !
You are welcome:p

---

### Post by DarkAngel88 on 2006-01-14
Once again, works like a charm !!  

The line was "iface eth0 inet dhcp" 

Now the system boots a lot faster !!

Thank you healychan, you saved my ubuntu partition :P

---

### Post by healychan on 2006-01-14
[QUOTE=DarkAngel88]Once again, works like a charm !!  

The line was "iface eth0 inet dhcp" 

Now the system boots a lot faster !!

Thank you healychan, you saved my ubuntu partition :P[/QUOTE]
I am really happy that I can help. I saw that many people having the same problem with you. They installed ndiswrapper and driver but didn't configure it.

Please put a tick for your thread to indicate that this problem have been solved. So others can refer to this thread as a guide.

---

### Post by healychan on 2006-01-14
Try to summarise your experience and produce a HOWTO if you have time.

I believe it can helps so many people whose share the same problem with you. Every 30 mins you will see a new thread with a topic of "wireless problems", "wireless card not working"............

There are so many resources on wiki and starter guide, I couldn't understand that why they always post a new thread.

---

### Post by trubblemaker on 2006-01-15
thank you for the tip, 
I had the same issue, 
that 4mins waiting for the interface to boot is killer when you need to get something of your computer quickly.

---

