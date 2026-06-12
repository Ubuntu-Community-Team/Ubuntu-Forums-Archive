---
title: "Strange network Issues"
date: 2005-12-06
forum: Desktop Environments
---

### Post by jcooper on 2005-12-06
I have just finished installing Breezy on my Toshiba M2 laptop (I've been an Ubuntu desktop user since Hoary).

I am finding I am having intermittent network difficulties using both the wired and wireless network connections - for e.g. I sometimes fail to connect to websites, gb's update mirror, google etc while other addresses on the internet are fine.

There are no obvious inconsistencies anywhere - what could be causing these problems? IPv6? DNS just appears to refuse to resolve some addresses.

This, by the way, is using both "normal" and Network-manager managed network connections.

Can anyone shed some light? It is very frustrating!!

---

### Post by moberry on 2005-12-06
I have had DNS resolution issues on my computers (My ISP's fault) Happens on  windows also. I just run my own bind server.

apt-get install bind

you will also have to tell your dhcp client not to overwrite your /etc/resolv.conf

i have dsl, i do this by commenting out "usepeerdns" in my provider file.

---

### Post by jcooper on 2005-12-06
My DNS issues only happen on the Ubuntu laptop - I can have my XP laptop from work next to it accessing all the URLs Ubuntu cannot...

Is there any way I can start hunting down the issue?

Its not related to just websites - I've had to change gb.ubuntu to uk.ubuntu to install software, and even after successfully visiting a web site, a few minutes later I'll be unable to!

So very frustrating!!!

---

