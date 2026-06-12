---
title: "Ethernet not connecting"
date: 2005-12-19
forum: General Help
---

### Post by Masteroc on 2005-12-19
I have just installed ubuntu 5.10 and in the installation skipped the auto configuration of the DHCP. When i started it up and ran it, i wanted to connect to the internet, so i went to System->administrator->networking and then clicked on my ethernet card (eth0). It said that it was not active. So i activated it. It activated, and i selected DHCP since i do not have a static ip. The machine would be connecting throught a router. Then i clicked ok. I tried firefox. It did not work. So, i restarted the machine. Still would not work. 

Any ideas

P.S. I was not able to expirement with this too long because my screen keeps freaking out on me (see my post [http://www.ubuntuforums.org/showthread.php?t=106076](http://www.ubuntuforums.org/showthread.php?t=106076))

---

### Post by greenway on 2005-12-19
Can you post the output of ifconfig?

---

### Post by Masteroc on 2005-12-20
ok, here are the results from ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:00:B4:9F:1F:E1
          inet6 addr: fe80::200:b4ff:fe9f:1fe1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:12
          TX packets:5 errors:7 dropped:0 overruns:0 carrier:14
          collisions:123 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2772 (2.7 KiB)
          Interrupt:11 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:72557 (70.8 KiB)  TX bytes:72557 (70.8 KiB)
```


What could be wrong with it?

I have checked, and the lights on the card are on, so it is getting power. It is not defective, becase it worked with the previous system that it was in.

---

### Post by Masteroc on 2005-12-20
should i try another ethernet card?

---

### Post by Masteroc on 2005-12-21
i just bought a new ethernet card. Installed it. 
And found out it did not work either!!!!

The network manager says that eth0 is active. It is not the card because i have tried 3 in the machine already. 

What could it be?

A setting?

---

### Post by greenway on 2005-12-22
So are you able to ping anything on your local network?? Is the light on your NIC on?

How are you connected to the internet? What are you using as your DHCP server?

Please run the command "sudo ifdown eth0" and then post the output of "sudo ifup eth0".

---

### Post by KurtB on 2005-12-22
Maybe this:

If you're connected directly to your  modem (not using router between modem an your PC), you sometimes have to reboot it in order to get an IP-adres.

This is what I had to do with my modem: my internetsubscription only "includes" 1 IP-adres,...so when I used Windows and reboot in ubuntu I've got to restart the modem to get a new lease...

---

### Post by Masteroc on 2005-12-22
Hi,

I got the Ethernet Card working. The new one that is. I just installed it, then it would not work, after that i just restarted the computer and it worked fine from there. 

Thanks for all your help!!  :KS

---

