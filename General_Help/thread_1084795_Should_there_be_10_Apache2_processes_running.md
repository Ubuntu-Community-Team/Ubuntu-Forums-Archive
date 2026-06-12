---
title: "Should there be 10 Apache2 processes running?"
date: 2009-03-02
forum: General Help
---

### Post by linuxNewb on 2009-03-02
I recently setup an Ubuntu server for the first time. I'm having a problem where certain (GET) requests are taking over 1 to 2 minutes. I've ruled out mysql queries, and php errors, etc.

It mostly (but not always) happens with ajax GET requests. These also happen to be the most process-intensive calls, though my memory usage never goes over 50%.

In my apache2.conf file I have set Apache2 to run as 'apache:apache'. ps shows that 'root' has 1 apache2 process running, and 'apache' has like 9 apache2 processes running. Is that normal? 

Also if anyone has any troubleshooting suggestions, other than traceroute, viewing apache2 and php logs, and ruling out mysql queries, I would love to here them. Thanks in advance.

---

### Post by raptor2552 on 2009-03-02
> In my apache2.conf file I have set Apache2 to run as 'apache:apache'. ps shows that 'root' has 1 apache2 process running, and 'apache' has like 9 apache2 processes running. Is that normal?


This is normal. The first process is always started and owned by init, the parent process from which all other processes start. The others are started by apache in preparation to receive requests from the web server.

This is what mine looks like. Notice process 6207 has parent process 1 (init) and 6284, 6285, 6286... have a parent id of 6207 (in your case apache):

root      6207     1  0 05:38 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  6284  6207  0 05:38 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  6285  6207  0 05:38 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  6286  6207  0 05:38 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  6287  6207  0 05:38 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  6288  6207  0 05:38 ?        00:00:00 /usr/sbin/apache2 -k start


I don't know why GET requests should take so long, network connect speed, something keeping the web server busy, etc. Is this on the internet or a intranet home office setup?

---

### Post by linuxNewb on 2009-03-03
Thanks for your response. The site is on the internet, but I just uploaded it, so there's no traffic to speak of. It's weird because when it does happen, even though the resulting page may take over 3 minutes to load, the processing happens really quick. Like if I submit the login form, then click a link right after clicking submit, the resulting page shows me being logged in (even tho it would have taken 3 minutes for the 'logged in' page to load if I hadn't clicked some link.

It almost always happens with AJAX calls. I tried turning off KeepAlive in the Apache2 config, but the problem remains. I get no errors, and the Apache2 access log shows 200 codes, it just takes for ever to send (or complete) the responses.

---

