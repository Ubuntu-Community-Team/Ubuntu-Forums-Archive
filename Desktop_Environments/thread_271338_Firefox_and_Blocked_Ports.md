---
title: "Firefox and Blocked Ports"
date: 2006-10-04
forum: Desktop Environments
---

### Post by taliskar on 2006-10-04
](*,) 

From my Ubuntu 6.06 LTS Desktop system, I'm trying to use Firefox to access websites that use non-standard ports.

For example:

[http://www.somemachine.com:8080](http://www.somemachine.com:8080) (web server listening on port 8080)

or

[http://www.somemachine.com:10000](http://www.somemachine.com:10000) (Webmin)

I cannot access these sites from Ubuntu.  I've tried Firefox to no avail and also did a 'telnet [www.somemachine.com](www.somemachine.com) 8080' to see if I would get a connection but nothing there either.

Through some testing, I've narrowed the issue down to starting at port 1000.  When I set up an apache web server to listen on TCP 999 or lower, I can connect fine.  But, when I set the web server listening port to TCP 1000 or higher, I cannot connect from my Ubuntu OS.  However, on this dual-boot laptop, when I try to access the same site from my Windows XP OS, I can get to it (and the other inaccessible URL's) just fine.

On a different live server, I am able to connect to a web server listening on TCP 80 but not to a different server listening on TCP 10000 (even though I can successfully access both sites when connecting from a Windows OS system).

I've turned on and tested and off and tested the Firestarter firewall, installed and uninstalled Webmin so I could use it to explicitly permit traffic to those high ports with Iptables.

None of it worked.  It truly seems to be something else in Ubuntu that is limiting access to those high ports.

Any ideas or is this a bug?

Thanks,
Taliskar

---

### Post by dcstar on 2006-10-05
> **taliskar said:**
> ](*,) 

From my Ubuntu 6.06 LTS Desktop system, I'm trying to use Firefox to access websites that use non-standard ports.
.......
None of it worked.  It truly seems to be something else in Ubuntu that is limiting access to those high ports.

Any ideas or is this a bug?

Thanks,
Taliskar

Never heard of anything like this before, but you may want to try disabling IPv6 and see if that has any effect (do a forum search).

---

### Post by clarknova on 2006-10-05
I'm using firefox in ubuntu, default settings, and I have no problem accessing my webmin server on port 10000 or apache on 8777. Can't imagine what's going on there.

---

### Post by taliskar on 2006-10-07
I tried shutting off IPv6 and that had no effect on my issue.  

But I was able to narrow it down to an issue with my wireless card.   I'm using an Inspiron 630m and with my wired connection, I don't experience any difficulty using higher ports with a browser (port 8080 for a web server, 10000 for webmin, etc).  But, with my wireless connection, I cannot access ports above 999 using any application (web browser, telnet for testing, etc.).

So, I'll report this as a bug.

---

### Post by rogier.de.groot on 2006-10-07
Please run "sudo iptables -L" and post the output, this sounds like firewall trouble...

---

