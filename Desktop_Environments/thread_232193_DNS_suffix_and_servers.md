---
title: "DNS suffix and servers"
date: 2006-08-08
forum: Desktop Environments
---

### Post by petec on 2006-08-08
I use NetworkManager for managing my laptop's wireless and wired networking.  At work, we have 4 different dns suffixes .  In windows I was able to append all 4 dns suffixes and manually set the dns server ip.  Is there a way to do this in NetworkManager?  I went into /etc/resolv.conf, but it seems that NetworkManager manages this file, and does not pick up changes to it.  Any ideas?

---

### Post by cmnorton on 2008-01-30
On Ubuntu 7.10, you should be able to go into System -->Administration --> Network, and even if you're set up for roaming, you can enter search criteria, which gets written into /etc/resolv.conf.

---

### Post by thegreedyturtle on 2008-02-12
To clarify a bit for people:
Go to System > Administration > Network
Click the DNS tab
In the search domains box, click add.
Add the DNS suffixes you want to append.

For example: if you add "google.com" and write mail in your browser window, it will append the DNS Suffix and direct you to mail.google.com, aka Gmail!

Very handy for people who work within a domain.

---

### Post by Sarmacid on 2008-07-17
Other way you can do this (console) is editting the /etc/resolv.conf file and add:

```
search yourdomain.com
```

Network manager is not changing this file so every time I boot it's the same, maybe it's because I have a static ip.

---

