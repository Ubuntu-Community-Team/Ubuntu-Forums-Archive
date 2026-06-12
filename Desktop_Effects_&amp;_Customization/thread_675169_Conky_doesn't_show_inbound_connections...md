---
title: "Conky doesn't show inbound connections.."
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by Spitphire on 2008-01-22
Ok, so my .conkyrc is pasted together from various sources.  My problem is the below code doesn't show any inbound connections.  It always says 0 and it never lists anything out. 

wlan0 is my device..

```
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${color #246eb5}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
```

Any ideas? It doesn't list anything...

---

### Post by ozmark on 2008-01-24
Perhaps wlan is your issue, look at the following for suggestions;

[http://members.cox.net/tonyt/d830/#conky](http://members.cox.net/tonyt/d830/#conky)  <-- nice .conky_rc here.

compile from source...
./configure --prefix=/usr --enable-wlan
make
make install

[http://ubuntuforums.org/archive/index.php/t-563401.html](http://ubuntuforums.org/archive/index.php/t-563401.html)

Good luck.

---

### Post by Spitphire on 2008-01-24
hmm.. i checked it out, but it looks like I have the wireless features installed.  I use conky to display a lot of info about my wlan settings.. any other ideas?

```
am@lp:~$ conky -v
Conky 1.4.7 compiled Thu Sep  6 11:25:25 GMT 2007 for Linux 2.6.15.7 (i686)

Compiled in features:

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * hddtemp
  * portmon
  * rss
  * wireless

```

---

### Post by Contivity on 2008-05-20
I'm also having the same problem. The problem I found is that most incoming connections are on tcp6. Try go to /etc/ssh/sshd_config then uncomment the:

Listen 0.0.0.0

So that it forces the SSH server to listen in ipv4 mode. This solves my problem.

---

### Post by bubbalouie on 2008-06-09
Extending on what Contivity said, I had the same issue, however, I disabled IPV6 for my entire system, link with instructions below:

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

It seems to have worked for me...

Good luck :)

---

