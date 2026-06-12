---
title: "CIsco Packet Tracer for Ubuntu"
date: 2012-10-27
forum: Education &amp; Science
---

### Post by x_master222 on 2012-10-27
Hello, I am running the newest Ubuntu 64-bit and I need Packet Tracer ... I found out that there was .deb package of Packet Tracer, but I cant find it on netacad page.
Does anyone have .deb of Packet Tracer? Or anyone knows how to get it .. is it still available also for Ubuntu ?

---

### Post by aabed91 on 2012-10-27
You can download it from here:
[http://www.mediafire.com/?r95gqy7n331ht8t](http://www.mediafire.com/?r95gqy7n331ht8t)

then go to terminal and type the following commands:

```
sudo sh PacketTracer533_i386_installer-deb.bin
```

then:

```
sudo ./PacketTracer533_i386_installer-deb.bin
```

the download start.

---

### Post by Lars Noodén on 2012-10-27
What about wireshark?

---

### Post by aabed91 on 2012-10-27
> **Lars Noodén said:**
> What about wireshark?

You can download it using this command:

```
sudo apt-get install wireshark
```

---

### Post by x_master222 on 2012-10-28
It installed PacketTracer, but when I want to run it, so I click on PacketTracer it does not start.

---

### Post by El Tito on 2012-11-17
Hi.
I had the same problem. It is due to running a 32bit application under a 64 bit system.
In my case, I installed:

*$sudo apt-get install ia32-libs-gtk*

and that solve my problem. Info about that library [here]("http://packages.debian.org/sid/ia32-libs-gtk").

Tell us if you succeed. Good luck!

---

### Post by El Tito on 2012-11-17
The previous details are commented here, just in case the above does not solve your problem. Maybe you didn't give the execute permission to the executable.

[http://www.ubuntubuzz.com/2011/05/installing-and-running-cisco-packet.html](http://www.ubuntubuzz.com/2011/05/installing-and-running-cisco-packet.html)

---

### Post by Dannation on 2013-04-26
> **aabed91 said:**
> You can download it from here:
[http://www.mediafire.com/?r95gqy7n331ht8t](http://www.mediafire.com/?r95gqy7n331ht8t)

then go to terminal and type the following commands:

```
sudo sh PacketTracer533_i386_installer-deb.bin
```

then:

```
sudo ./PacketTracer533_i386_installer-deb.bin
```

the download start.



You sir are a saint, worked perfectly, although I didn't need to enter the second command, I just did the first one and now it is installed :D

---

### Post by Sef on 2013-04-29
Packet Tracer is proprietary and cannot just be downloaded legally, so locked.

---

