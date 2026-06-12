---
title: "[SOLVED] Cups problem"
date: 2009-01-10
forum: General Help
---

### Post by svsig on 2009-01-10
I have installed Ubuntu 8.10 server, and I am now trying to install CUPS. I have tried to follow several How-To's found on the web, but I can't make it work. When I try to access the web interface at [http://server:631](http://server:631) from another machine in the network I get an error message: Failed to connect. I have installed LAMP server and MediaWiki, and these things are working fine.

I have basically tried to follow the description in [_this how-to_]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller-p2"), under Installing CUPS. This is for 7.10, but it is the best one I have been able to find.

Does anybody have a good suggestion?

---

### Post by schilcha on 2009-01-10
I've looked at the suggestions in the how-to and compared them to my cups-configuration. Two things you might try:
1) Instead of using a specific IP-address in the listen-parameter, use
```

Listen 0.0.0.0:631

```
This will make cups listen on all network interfaces. (it seems that there is an error in the how-to, but I might be wrong).

2) I allowed my local network to access cups. My admin-access-section looks like this (note the difference in the Allow-statement):
```

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow 10.42.42.0/24
</Location>

```

Good Luck,
  schilcha

---

### Post by svsig on 2009-01-11
I tried no. 1 first, and it worked! I can access the CUPS web interface!

Thanks a LOT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

