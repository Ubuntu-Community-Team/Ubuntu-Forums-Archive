---
title: "111 Connection Refused ?!!"
date: 2009-05-28
forum: General Help
---

### Post by matey3 on 2009-05-28
Hello All:

I am getting this error 111 connection refused message from my Ubuntu9 machine which was working fine yesterday but now without me doing anything it will Not go on the Internet and it will Not get apt-get anything?!
I am using Firefox but cant get anything else right now anyway! I cannot get lynx either so I am sure even if I had lynx installed I still couldnt get on the Net. (I only get local intranet)

I think may be someone has put this machine' MAC address in a black list or something? I do get IP address and can ping other machines in & outside of our LAN.

Has anyone seen this before? Any solutions??

Thank You!

PS , BTW I changed my IP and gave it a different and static to no avail!

---

### Post by albinootje on 2009-05-28
> **matey3 said:**
> I do get IP address and can ping other machines in & outside of our LAN.

Please post the following :
```

ping -c3 194.109.21.51
cat /etc/resolv.conf

```

---

### Post by matey3 on 2009-05-28
Thanks I do get 3 send and 3 received message from ping you sent.
The resolv.conf is setup right. (with domain name, search ,and nameserver IP address).

---

### Post by albinootje on 2009-05-28
> **matey3 said:**
> Thanks I do get 3 send and 3 received message from ping you sent.
The resolv.conf is setup right. (with domain name, search ,and nameserver IP address).

If you can ping a public ip address, and you cannot use the internet in various applications, and you cannot ping a website, then your DNS settings in /etc/resolv.conf (or NetworkManager for that matter) are the problem.

Can you try the OpenDNS DNS servers ?
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by matey3 on 2009-05-28
> **albinootje said:**
> If you can ping a public ip address, and you cannot use the internet in various applications, and you cannot ping a website, then your DNS settings in /etc/resolv.conf (or NetworkManager for that matter) are the problem.

Can you try the OpenDNS DNS servers ?
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

Thank you for the help.
I'll give it a try.

I was thinking may be it was a Firefox problem but that is Not the case since I cannot get any updates or run apt-get install at all.
Someone has probably blocked some ports for my Linux machine, (this is my windowz pc) I even switched cables (changed names on my linux box etc, etc, to no avail).
I'll mess with the DNS stuff like this site shows, hopefully I learn something before the day is over?!
lol

Thanks a lot.

---

