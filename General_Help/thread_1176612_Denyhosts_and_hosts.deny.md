---
title: "Denyhosts and hosts.deny"
date: 2009-06-02
forum: General Help
---

### Post by ericinwisconsin on 2009-06-02
Ok, I screwed up and failed to ssh into my home box too many times. Now denyhosts has blocked my work IP address. Fair and good; that's my own fault.

So I logged in from another IP address and removed my work IP addy from the /etc/hosts.deny file. It kept reappearing in the file! So I removed all references to my work IP from the /var/log/denyhosts and /var/log/auth.log files. STILL it adds my work IP to the /etc/hosts.deny file.

I'm assuming that denyhosts is finding my work IP somewhere else and adding it? What am I missing?

---

### Post by ericinwisconsin on 2009-06-08
Ok, I found the solution myself. For anyone else who encounters this problem, here's what to do:

1. Stop the denyhosts daemon:
```

/etc/init.d/denyhosts stop

```

2. Remove the IP address from /etc/hosts.deny
3. Remove the IP address from /var/lib/denyhosts/hosts-restricted
4. Start the denyhosts daemon:
```

/etc/init.d/denyhosts start

```

I found the solution for this here:
[http://ubuntuforums.org/showthread.php?t=361053](http://ubuntuforums.org/showthread.php?t=361053)

But apparently the default location of the data files has been moved from /usr/share/denyhosts/data to /var/lib/denyhosts sometime in the recent past. You can always veryify where that directory is by finding the WORK_DIR variable in /etc/denyhosts.conf.

Hope this helps someone else!

---

