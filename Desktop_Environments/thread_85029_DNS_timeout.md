---
title: "DNS timeout?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by kaaredyret on 2005-11-01
On 5.10 I have this weird problem. On my Ubuntu box, almost every time I enter an address in Firefox (or click on a link from a new website), I immidiately get this message that the page cannot be displayed. If I try once again (refresh), Firefox connects successfully to the web site.

When I use Windows XP on the very same machine, this is not a problem at all.

What can I do? Is some timeout value too small?

---

### Post by HermanAB on 2005-11-01
Probably a slow DNS listed in /etc/resolv.conf

Two solutions:
a. Install BIND and run your own slave DNS.
b. Delete the top entry in /etc/resolv.conf, or move it to the bottom of the list of DNS.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by kaaredyret on 2005-11-01
**Oh thank you very much!** \\:D/

My computer is connected to a Windows 2000 machine with ICS (Internet Connection Sharing) enabled.

In /etc/resolv.conf I found only one line, a nameserver that was in fact my Windows 2000 IP address.

I entered two more DNS servers before that, the two DNS addresses my ISP recommend using.

Now it is lightning fast, finally!

---

