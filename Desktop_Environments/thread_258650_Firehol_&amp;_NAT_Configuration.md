---
title: "Firehol &amp; NAT Configuration"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Johnathon on 2006-09-16
Hi... I'm running a firehol on my PC, and I want to do somthing a bit fancy. Heres a basic diagram

Asterisk Server (work)
       |
       |
  VPN To Work Network
       |
       |
Home PC (running Dapper, OpenVPN + latest firehol)
       |
       |
Elmeg IP phone

As you can see, I want to use the VPN connection on my home pc, to link my phone to the asterisk server at work, to enable me to work from home with a work phone no. + extention.

Now, I think this has somthing to do with NAT routing, but I can't for the life of me figure out a way to get it to work. Heres the relevant config part atm:

nat to-source 192.168.0.11 outface tun0 dst 10.2.0.82
nat to-destination 10.2.0.82 inface eth0 dst 192.168.0.11

192.168.0.11 is the phone on my home network, 10.2.0.82 is my work asterisk server (connected on the tun0 interface).

Any ideas / tips?!

---

### Post by Johnathon on 2006-09-16
I hate doing this... :(  *bump*

---

### Post by Johnathon on 2006-09-17
:cry: Last one *bump*. I guess no-one can help then?

---

