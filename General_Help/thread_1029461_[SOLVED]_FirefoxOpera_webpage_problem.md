---
title: "[SOLVED] Firefox/Opera webpage problem"
date: 2009-01-03
forum: General Help
---

### Post by toni_uk on 2009-01-03
I have installed Xubuntu on my machine to test a setup I want to to for my in-laws. Everything went well until I realised I have a problem loading some pages on Firefox. Those pages are:

[http://www.skype.com](http://www.skype.com)

and funnily enough

[http://www.distrowatch.com](http://www.distrowatch.com)

There is no error message but they are just stuck on loading and finally timing out. I have then downloaded Opera and I am showing the same problem. A bit of research showed it could be a IPV6 issue. I therefore disabeled ipv6 in about:config and also /etc/modprobe.d/aliases - 'alias net-pf-10 ipv6' to alias 'net-pf-10 off ipv6'. No change - still can't get those pages loaded. Any help would be appreciated.

Thanks!

---

### Post by Scunnered on 2009-01-03
I had a look at what you say and can't replicate your problem. 

I use both browsers and using the hyperlinks provided by you each browser opened the pages in a twinkle of an eye.  Suggest that you try things again as it looks like you just lucked out when you tried.

Hope it works for you when you retry

---

### Post by toni_uk on 2009-01-03
Thanks Scunnered. I have logged out and back in several times. Still the same problem. On my Fedora 10 install Firefox works without any problem. Did you try it on Xubuntu?

---

### Post by Scunnered on 2009-01-03
No I am strictly Ubuntu.

---

### Post by toni_uk on 2009-01-03
Scunnered, it works fine under ubuntu - Xubuntu seems to be the problem

---

### Post by waj1122 on 2009-01-03
The links work just fine on Xubuntu. I'm running Xubuntu as a dual boot on my laptop along with Vista. This might not be the problem but it's worth a try. Completely clean out your cookies and cache (both in Firefox and Opera), then restart Firefox or Opera, whichever you prefer. If that doesn't work try recycling your modem.

---

### Post by toni_uk on 2009-01-04
solution found on Linuxquestion. There seems to be a bug on NetWorkManager 0.7. Installed and using wicd instead. Works a treat. Thanks for all your replies.

[http://www.linuxquestions.org/questions/linux-software-2/firefox-opera-webpage-problem-not-loading-694752/](http://www.linuxquestions.org/questions/linux-software-2/firefox-opera-webpage-problem-not-loading-694752/)

---

