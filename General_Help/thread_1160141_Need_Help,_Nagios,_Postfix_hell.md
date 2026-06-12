---
title: "Need Help, Nagios, Postfix hell"
date: 2009-05-15
forum: General Help
---

### Post by kristiaan_d on 2009-05-15
Hi guys,
firstly i need to say i am a REALLY new beginner to linux and so far everything i have done has worked great, however things are sent to try us and so far i really want to cry...


I know this is because i am a beginner and its down to the fact i am not quite understanding something going on, but i cannot work out what is going wrong.

Basically i have installed and got Nagios working on a completely clean and minimal install of ubuntu 9.04 server edition. Presently it does not send me email notifications when something falls over.

I am trying to get postfix running as a bog standard SMTP relay so that when Nagios generates an email to send POSTFIX will authenticate with our production mail server and send the email.

But for the life of me i CANNOT get postfix working so far i have far gone through dozens of different blogs, links and other websites telling me how to configure postfix but none of them seem to be able to give me a basic simple to follow set of instructions to get postfix working as a basic relay. (not even worried if its an open relay as it will be internal to our private network).

---

### Post by dcstar on 2009-05-15
> **kristiaan_d said:**
> 
..........
But for the life of me i CANNOT get postfix working so far i have far gone through dozens of different blogs, links and other websites telling me how to configure postfix but none of them seem to be able to give me a basic simple to follow set of instructions to get postfix working as a basic relay. (not even worried if its an open relay as it will be internal to our private network).

Edit the main.cf file to accept connections from your local network, this says to accept from a 192.168.0 network:

```
mynetworks = 127.0.0.0/8 192.168.0.0/24
```

---

### Post by kristiaan_d on 2009-05-18
Thanks for the reply, its all working now, this was part of the problem. i had been looking at it for so long i had started to ignore it assuming it was correct....


needed a few other tweaks to get it running but it was as i suspected my inexperience with linux.


Cheers guys i always get great help from you!!!

Kris

---

