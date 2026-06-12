---
title: "internet slow again"
date: 2005-10-03
forum: Desktop Environments
---

### Post by zac851 on 2005-10-03
I was having problems with the browser being extremely slow when I was using the Konkuror browser  So I swithched to mozilla browser.   I also went off  the directions below on ubuntu guide on speeding up mozilla. This helps ALOT but every 10-15 minutes only certain websites (ones that I load everyday) will work while other websites (new ones) will not work and just say  "Resolving www.nameofwebsite.com"   and eventually time out.  Any ideas guys?     I know its not my internet connection cause it only does this when I boot to linux. Thanks.

   1. Read General Notes
   2. Applications -> Internet -> Firefox Web Browser
   3. Mozilla Firefox

Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

   4. Restart Mozilla Firefox

---

### Post by zac851 on 2005-10-03
Man I'm so tired of this.   It worked good for one day.  Then just got slow again.  I really like linux and havent logged into windows in days, but this slow internet browsing is enough to make me not even want to use linux since web browsing is 98% of what I do on the internet.   It takes nearly 20 seconds looking up the website before beggining to load it.   I don't know what else to do????

---

### Post by cwaldbieser on 2005-10-03
[QUOTE=zac851]Man I'm so tired of this.   It worked good for one day.  Then just got slow again.  I really like linux and havent logged into windows in days, but this slow internet browsing is enough to make me not even want to use linux since web browsing is 98% of what I do on the internet.   It takes nearly 20 seconds looking up the website before beggining to load it.   I don't know what else to do????[/QUOTE]
If you feel like trying Konqueror again, I found a post on the forums that really sped it up for me.
```

$ sudo bash
# echo "KDE_NO_IPV6=true" >> /etc/environment

```
Exit KDE and log back in.  Konqueror goes lightning fast!

Not that I'd reccommend it for most of your browsing, but just as a test to see if the problem is with the browser or with your network configuration, could you try using the text based "lynx" from the terminal to see if that also takes a long time loading your pages?

---

