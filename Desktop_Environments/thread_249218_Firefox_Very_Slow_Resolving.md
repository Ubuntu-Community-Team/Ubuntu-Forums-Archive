---
title: "Firefox Very Slow Resolving"
date: 2006-09-02
forum: Desktop Environments
---

### Post by the_0ne on 2006-09-02
I'm having a problem with firefox being very slow.  Distribution is Dapper 6.06, Firefox version is 1.5.0.5.  I have 2 machines and the one is extremely fast, so it's not my ISP.  What is happening is just resolving pages is taking forever.  FF just sits there with "Looking up ..." message for several seconds and then finally resolves.  And even then the page can take from several seconds to a couple of minutes to come in.

What's really strange if I open up a terminal and ping the site, it resolves instantly.  It's only ff that is taking forever to resolve.

Of course I've tried several pages and it's every page I've tried.  This is only on one of my machines, the machine I have upstairs (which is on the same network) is fine.

---

### Post by tribaal on 2006-09-02
try the following trick:

- open firefox
- In the adress bar type in "about:config"
- In the filter bar type in "ipv6"
- Double click "network.dns.disableIPv6" so that the value turns to TRUE
- Restart firefox


Hope this helps you out... worked for me at least.

- trib'

---

### Post by the_0ne on 2006-09-02
> **tribaal said:**
> try the following trick:

- open firefox
- In the adress bar type in "about:config"
- In the filter bar type in "ipv6"
- Double click "network.dns.disableIPv6" so that the value turns to TRUE
- Restart firefox


Hope this helps you out... worked for me at least.

- trib'

Dude, you rule!!!  I would have never found that.  That did it.  I am delicious'ing that link, that's for sure.  Thanks.

---

### Post by habtool on 2006-09-02
To make it system wide:
If you're using Dapper Drake edit /etc/modprobe.d/aliases, comment out the existing alias net-pf-10 ipv6 and add alias net-pf-10 off, like so:

alias net-pf-10 off
# alias net-pf-10 ipv6

Reboot.

[http://www.ubuntuforums.org/showthread.php?t=87798&page=5](http://www.ubuntuforums.org/showthread.php?t=87798&page=5)

---

### Post by mikq on 2006-09-05
Hey I had the same problem and was just reviewing the posts and I came accross this one. I did the system wide fix and it worked like a charm.
Thanx
Mike

---

