---
title: "Security Advice"
date: 2006-01-14
forum: Desktop Environments
---

### Post by cajunaggie on 2006-01-14
What security programs do you guys (and/or gals) have running to keep you safe from all the wee-bugger beasties the Net has on it? Firewalls? anti-virus? What do you have going?

---

### Post by kingsidy on 2006-01-14
firestarter-->firewall
clamAV--> antivirus
chkroot--> some sort of anti-spyware for linux.(rootkits)

---

### Post by qferret on 2006-01-14
I used to use F-Prot for AV software, but these days I have Aegis installed....No particular reason.... both seem alright

---

### Post by Mr_Grieves on 2006-01-14
Generating a IP-Tables firewall is easy: [http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)
Tripwire keeps track on rootkits and files: [http://sourceforge.net/projects/tripwire/](http://sourceforge.net/projects/tripwire/)
Clam Anti Virus.. Mm.. clam.. [http://www.clamav.net/](http://www.clamav.net/)

Free security stuff for Linux: [http://www.thefreecountry.com/security/antivirus.shtml](http://www.thefreecountry.com/security/antivirus.shtml)

---

### Post by cajunaggie on 2006-01-15
I installed ClamAV but I don't know any of the line commands for it. Is there a place that I can find them?

---

### Post by cutOff on 2006-01-15
Rootkit Hunter

> Rootkit scanner is scanning tool to ensure you for about 99.9%* you're clean of nasty tools. This tool scans for rootkits, backdoors and local exploits by running tests like:

- MD5 hash compare
- Look for default files used by rootkits
- Wrong file permissions for binaries
- Look for suspected strings in LKM and KLD modules
- Look for hidden files
- Optional scan within plaintext and binary files

Rootkit Hunter is released as GPL licensed project and free for everyone to use.

* No, not really 99.9%.. It's just another security layer

```
sudo aptitude install rkhunter
```

---

### Post by AAUU on 2006-01-15
iptables.  That's about all you'll need if you don't go crazy downloading suspicious binaries.

For fun you can:  
sudo lsof -i 

This will tell you what's listening.

localhost.localdomain = stuff listening on loopback (127.0.0.1) and not accesible from the internet

*:someword or someport number = stuff that anyone can connect to if there's no firewall in place

IPADDRESS:someword or someport number = stuff listening only on that IP address which means it's available to anyone that can connect to that IP.  Again, firewall rules permitting.

---

### Post by ardchoille on 2006-02-10
I use rkhunter, chkrootkit and tripwire. But, there are tons of good security apps for Linux.

---

