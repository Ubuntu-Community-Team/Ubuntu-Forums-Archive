---
title: "Localhost!!!"
date: 2006-05-30
forum: Desktop Environments
---

### Post by barbz127 on 2006-05-30
Im hoping this is going to be simple but i cant access localhost on my 5.10 machine. it goes straight to a website promoting p2p type software - havent touched any of the setup of firefox so dont know whats going down.
Ive installed sophos antivirus so trying to access the console for it.

Cheers

---

### Post by DeadEyes on 2006-05-30
run the ifconfig command and check the inetaddr given for the local loopback it should be somthing like:
inet addr:127.0.0.1 Mask:255.0.0.0
if it's not try 
$sudo ifconfig lo 127.0.0.1

Edit:
fix mistake as pointed out by [email]index_0@ya.com[/email] and Sukarn
whoops

---

### Post by index_0@ya.com on 2006-05-30
a doubt, 
is it iconfig or ifconfig ?

---

### Post by Sukarn on 2006-05-30
Its ifconfig

---

