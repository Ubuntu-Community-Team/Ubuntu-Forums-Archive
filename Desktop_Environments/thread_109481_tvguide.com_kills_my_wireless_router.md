---
title: "tvguide.com kills my wireless router"
date: 2005-12-28
forum: Desktop Environments
---

### Post by cwmccabe on 2005-12-28
Strange problem, maybe.  :confused:   Whenever I try to view [www.tvguide.com](www.tvguide.com) in Mozilla Firefox it locks up my router (Netgear WGR614.v3).  This has also occurred on a few other websites (ex [www.aaa.com](www.aaa.com)) but I've most recently seen it on tvguide.com.  I'm running Ubuntu 5.10 on a Toshiba Satellite L35-S119.

This is the -consistant- pattern:

1. I go to the website, here tvguide.com

2. I get booted off the router

3. My "Connection Properties" panel shows that the router signal is still high, but I've lost connectivity.

4. All other computers wired-in and wireless, windows and linux also lose their connection.  But--when these other computers view tvguide.com they don't hose the router.

5. I power-cycle the router and deactivate/activate my wireless connection and I'm back connected again.


What can I do? I haven't seen this problem addressed in other forum threads yet.  Please let me know if there is any more information or output I can give.

(Maybe linux is just telling me that I watch too much tv? :???: )

Thanks for any hints!

---

### Post by cwmccabe on 2006-06-23
If it helps anyone, I *think* I solved the problem.  I used the info at the following URL to fix it:  [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

In my case, it wasn't that web browsing was slow--it was that my router would actually lock out all attached computers when I visited certain websites.  I had to restart the router every time it happened.

Anyone know if this is a documented bug?

---

