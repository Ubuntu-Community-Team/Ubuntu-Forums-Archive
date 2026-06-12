---
title: "Unknown Host"
date: 2005-12-24
forum: General Help
---

### Post by gamer46290 on 2005-12-24
I just wiped windows off of my computer and installed kubuntu. I have two computers, a macintosh laptop and the desktop computer I just installed kubuntu on. The internet works just fine on my lap top, the only browser that came with kubuntu is Konqueror, and it will go to some websites but the rest it will say unknown host. I searched this on google and it described what unknown host meant but I can't figure out how to fix this. Any help?? Thank-you

---

### Post by three_sixteen on 2005-12-24
[QUOTE=gamer46290]I just wiped windows off of my computer and installed kubuntu. I have two computers, a macintosh laptop and the desktop computer I just installed kubuntu on. The internet works just fine on my lap top, the only browser that came with kubuntu is Konqueror, and it will go to some websites but the rest it will say unknown host. I searched this on google and it described what unknown host meant but I can't figure out how to fix this. Any help?? Thank-you[/QUOTE]

No idea, but my first shot would be to try using a different browser.  Try using firefox maybe?

---

### Post by gamer46290 on 2005-12-24
How do I use a different browser when I only have konqueror on my system, and I can't use the internet to download a new one?

---

### Post by tuxy on 2005-12-24
If you can post more information it will be greatful. Can you access internet from your desktop ? Can you ping a website from the console ? If you can ping the website but you can't open it then it might be DNS problem. Have a look in **/etc/resolv.conf** if the nameserver exists.

If you want to install Firefox web browser. Do **apt-get update** first then **apt-get install firefox**

---

### Post by gamer46290 on 2005-12-24
I put in that one code you said to put and it says name server 192.168.2.1,

and if this helps when i go to network settings it says my IP address is 192.168.2.2 and the protocol is dhcp a green check mark next to enabled ethernet network device.
 I have dsl internet, a dsl modem, and a router, the wireless internet on my lap top is working flawlessly.

---

### Post by tuxy on 2005-12-24
Can you ping a website from command console?

---

### Post by gamer46290 on 2005-12-24
How do I do that?

---

### Post by tuxy on 2005-12-24
Applications>Accessories>Terminal. When you open Terminal type 
**ping [www.google.com](www.google.com)** and post the results you get.

---

### Post by gamer46290 on 2005-12-24
Ok i'm doing that right now and it just keeps on putting
 64 bytes from 64.233.179.104: I amp_seq= (a number that keeps going up) t t l=245 time= (always a number with 38.)

---

### Post by timfrost on 2005-12-24
Since you can ping google, it isn't a DNS issue.

Terminate the ping, by hitting CTRL-C in the terminal session.

My guess is that konqueror isn't correctly handling some links.

Can you post an example URL that fails?

---

### Post by gamer46290 on 2005-12-24
Well some pages come up all the way or only part of the way, I just went to [www.download.com](www.download.com) and go the unknown host message.

---

### Post by gamer46290 on 2005-12-24
Hey! I managed to download firefox even though I am getting the unknown host message still, how do I install firefox??

---

