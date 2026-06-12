---
title: "Connection Refused"
date: 2006-01-27
forum: Desktop Environments
---

### Post by techsupportrich on 2006-01-27
Ive just downloaded and installed the latest version of ubuntu to my laptop. Everything seems to be working fine except when I try to view a web page, Im told connection refused. Im trying to get online through my ethernet port to my router. I can use firefox to interact with my router so I know its connected. Im also using the internet on another machine now so I know the ISP is fine. I just can't get internet connectivity on umbuntu. Can anyone help? I know this is a biggie, but without internet I have to go back to windows.

---

### Post by ]Nbx*cmD[ on 2006-01-27
Can you run ifconfig in a console and paste the output please?

---

### Post by techsupportrich on 2006-01-27
I dont think so, I have no idea what Im doing, this is my first Linux install. I also have no connectivity on my linux machine so I cant paste the data into anything you could see.

Just trying to think what Ive done...

Its a DLink router

Linux has an IP address from the router. 
It has the IP address of the router

If I load firefox and put in the IP of the router then I can access the menus on it.

There is no other connectivity. Ive tried a variety of configs including DCHP and putting in a static IP (dont think thats supposed to work)

Life's never easy is it.

---

### Post by ]Nbx*cmD[ on 2006-01-27
If you are using Gnome, Alt+F2 will open a small dialog box, type gnome-terminal there and that will open a terminal. In the terminal window just type ifconfig and transcribe here the output please :)

---

### Post by Peter76 on 2006-01-27
In System>????(sorry, using dutch version)>network, go to the dns tab and add the ip address of your router.

---

### Post by techsupportrich on 2006-01-27
richard@ubuntulaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:07:83:0A
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe07:830a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:487212 (475.7 KiB)  TX bytes:155312 (151.6 KiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1183860 (1.1 MiB)  TX bytes:1183860 (1.1 MiB)

richard@ubuntulaptop:~$

---

### Post by techsupportrich on 2006-01-27
Ive been into network settings and the DNS tab already has the router IP in it

---

### Post by GeneralZod on 2006-01-27
What happens if you 

```

ping www.google.com

```
?

What about 

```

ping 66.102.9.147

```
?

---

### Post by techsupportrich on 2006-01-27
it apears to ping both of those quite happily

---

### Post by techsupportrich on 2006-01-27
New developments....

I can now visit google if I do it by entering the IP address rather than by typing [www.google.com](www.google.com). I can visit other web pages if I do it by following links rather than typing in the address. 

I still cannot connect with any other program such as an IM client or mail program, or from the terminal.

---

### Post by techsupportrich on 2006-01-27
Anyone else got any ideas?

---

### Post by stream303 on 2006-01-27
[QUOTE=techsupportrich]Ive been into network settings and the DNS tab already has the router IP in it[/QUOTE]

I'd find out what the primary and backup nameservers of your isp are, and use those instead of relying on the one internal to the router.

---

### Post by techsupportrich on 2006-01-27
I hate to say it but I'm going back to windows.

---

