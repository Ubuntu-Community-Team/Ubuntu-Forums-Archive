---
title: "Problems connecting to Sky wi-fi"
date: 2007-08-14
forum: Dell  Ubuntu Support
---

### Post by katkin on 2007-08-14
We have just got Sky/BT broadband at home and my flatmate set up the wi-fi yesterday. Before that I could connect to the broadband via the Ethernet perfectly. Since she has set up the wi-fi I can connect to it (it shows 99% coverage etc.) but when I open Firefox it won't load any internet pages. The same happens if I just try to connect via the Ethernet too. It shows me as being connected to the internet, but I can't load any pages in Firefox, or my Thunderbird e-mail either.

I was just wondering whether I need to change any of the settings on my laptop. I have a Dell Latitude D620.

Any help would be much appreciated.

:confused:

---

### Post by Steve1961 on 2007-08-14
Sounds like it could be a dns issue.  Can you ping sites?

---

### Post by katkin on 2007-08-14
I'm not sure how to ping sites? I'm new to this technical malarkey-type-stuff. . . . sorry for being blonde. Could you be a bit more specific?

---

### Post by Steve1961 on 2007-08-14
Open a terminal and copy and paste the following:

ping -c 3 208.67.222.222

post the output here

---

### Post by katkin on 2007-08-14
Below is what it says in the terminal, however I am at work and connected to a wired network connection at work at the moment, rather than Sky wi-fi at home, so I'm guessing that would give different results. . . . Will I need to wait until I get home to do the same thing?

PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=55 time=1.85 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=55 time=1.49 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=55 time=1.45 ms

--- 208.67.222.222 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 1.456/1.601/1.853/0.184 ms

	:-?

---

### Post by Steve1961 on 2007-08-14
Yes, try the same thing when you get home.

---

