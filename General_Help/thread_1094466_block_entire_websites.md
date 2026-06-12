---
title: "block entire websites"
date: 2009-03-12
forum: General Help
---

### Post by wildman4god on 2009-03-12
I know how to block specific websites using etc/host file but I am trying to block a site called deviantart.com, now if I add 0.0.0.0 [www.deviantart.com](www.deviantart.com) to the file it blocks its home page, however each user's site is listed as [http://[username].deviantart.com](http://[username].deviantart.com). now if I add 0.0.0.0 [www.deviantart.com](www.deviantart.com) to the file, it won't block all the user's page is there any kinda wildcard that i can use in the /etc/host file so it blocks [http://[any](http://[any) user].deviantart.com

---

### Post by mb_webguy on 2009-03-12
Hosts files don't use wildcards, so there's unfortunately no way to do what you're asking using the hosts file.  For a system-wide solution, you'd have to use DNS.  For a local solution, you can use something like Firefox's Adblock Plus extension.

---

### Post by rybl on 2009-03-12
Unfortunately the hosts file does not support wild cards.  If there are only a few websites that the computer needs to access you could set your DNS server to 127.0.0.1 and manually put in the IP addresses of allowed sites.  This is not an ideal solution however since some sites may have multiple IP addresses or have IP addresses that change. Your best option is probably to install some sort of content filtering software.

---

