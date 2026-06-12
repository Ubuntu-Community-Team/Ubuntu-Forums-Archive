---
title: "some pages load slow on firefox, opera, konqueror"
date: 2009-01-22
forum: General Help
---

### Post by svrkispm on 2009-01-22
hello, i have the following problem:
i generally use firefox, atm 3.0.5. I noticed, that there are some webpages, that load terribly slow (8-10 minutes). I have no idea what the reason might be.
I tried the same pages in other browsers (Opera 9.63, Konqueror) - they still load very slow. To my big surprise they load really fast in links. I tried to run some browsers from my windows installation (opera, firefox) - works fine. My pc has the same network configuration in windows as in linux. Then i tried to use GET from terminal - works ok. Then i tried to connect with internet explorer from windows xp running in virtualbox on my linux with some default nat networking - works fine.

One more thing - there is no active content on one of these pages (no flash, no javascript, just plain html), but there is some small flash on the another one. But that doesnt seem to be the problem.

some other possibilities i have already excluded:
* problem on the other side - works well for all my friends
* dns - works as it should, nslookup resolves all domain names correctly and fast
* some strange network problems - ping is ok (1-2ms), tcpdump shows reasonable network communication and response from other side, just the browser doesnt show anything
* slow connection - i have 100 mbit
* /etc/hosts - ok

so to sum up - all my linux GUI browsers seem to have this problem. idk why.

my system is kubuntu 8.10
uname -a : Linux zer0 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

can you give me any hints, what the problem might be or what else to check for? thank you.

---

### Post by svrkispm on 2009-01-22
anyone? at least some hints what else to check? i am really stuck :/

---

### Post by svrkispm on 2009-01-23
solved - problem seems to be associated with ntop daemon, no idea when or why i have installed that, and no idea why it causes this. :cool:

---

