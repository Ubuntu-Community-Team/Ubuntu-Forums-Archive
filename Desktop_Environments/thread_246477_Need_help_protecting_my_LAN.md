---
title: "Need help protecting my LAN"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Aglarond on 2006-08-29
Ubuntu seems to have a great community, so maybe you guys can help me. Currently I'm using an OpenBSD machine for my internet firewall/router. All it does is packet filtering and assigning IPs to my internal boxes. All of the machines are either Ubuntu or Gentoo, so I haven't been too worried about anything else.

So, here's my problem: My wife is having to use a Windows machine for work now. I've already sequestered it on it's own DMZ, but I'm still worried about viruses, malware and all that. Are there any good opensource utilities you guys would recommend for scanning for that kind of thing? Since all traffic routes through the BSD box, I'd like to filter everything thing there, maybe using squid with some other utilities. Otherwise, I have to spend a bunch of money buying software I don't completely trust.

The software wouldn't have to run on BSD. If I found something good, I'd replace OpenBSD with Linux. Any help is appreciated.

Thanks
Mike

---

### Post by lagagnon on 2006-08-29
Clam AV.

---

### Post by Woei on 2006-08-29
> **Aglarond said:**
> Ubuntu seems to have a great community, so maybe you guys can help me. Currently I'm using an OpenBSD machine for my internet firewall/router. All it does is packet filtering and assigning IPs to my internal boxes. All of the machines are either Ubuntu or Gentoo, so I haven't been too worried about anything else.

So, here's my problem: My wife is having to use a Windows machine for work now. I've already sequestered it on it's own DMZ, but I'm still worried about viruses, malware and all that. Are there any good opensource utilities you guys would recommend for scanning for that kind of thing? Since all traffic routes through the BSD box, I'd like to filter everything thing there, maybe using squid with some other utilities. Otherwise, I have to spend a bunch of money buying software I don't completely trust.

The software wouldn't have to run on BSD. If I found something good, I'd replace OpenBSD with Linux. Any help is appreciated.

Thanks
Mike


Well, I still think the best security is an educated user. Make your wife security conscient, warning her about the dangers of opening exe files, opening mail attachment from unknown users and especially fishy ones from known people.

Step two is keeping her machine as up to date as possible. Keep on top of any security patches for both the OS and applications. Moreover, make the account your wife is using a *user* account instead of an administrator account. You're not browsing the web as root on a Unix machine either, are you ?

Lastly, pop the mail for her and let it run through a virusscanner like ClamAV, as already suggested. Squid already comes with a powerful 'acl' command which, combined with the equally interesting 'url_regex' command, allows you to filter out any files which may pose a problem: exe, vbs, cab, com, pif, etc.

All in all, a windows machine which is fully up to date, operated by a restricted user account isn't nearly as bad as some people make it out to be.

---

### Post by Aglarond on 2006-08-29
Thanks for the advice. She's very security conscious and I trust her not to open questionable files. ClamAV looks good, so I'll try setting that up when I get home.

---

