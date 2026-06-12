---
title: "limit speed in ProFTPd"
date: 2005-12-23
forum: General Help
---

### Post by otey on 2005-12-23
Is there a way to limit the speed of downloads and upload in proftp? 
Im sharing internet with my warcraft 3 - ultra dota gaming maniack, and he is complaining when I use all the bandwidth.

---

### Post by 23meg on 2005-12-23
I'm not sure about whether proftpd has the feature but if you figure that it doesn't, you can use trickle, which is a userspace bandwidth limiter that can limit the bandwitdh usage of individual apps. It's in the repositories.

---

### Post by otey on 2005-12-23
I found out by myself.. Sorry im so quick on the posting..

I found this config file on the page [http://www.linux-sxs.org/internet_serving/proftpd.html]("http://www.linux-sxs.org/internet_serving/proftpd.html")

```

# TransferRate RETR|STOR|APPE|STOU KBrate:freebytes 
TransferRate RETR 20:0 
# older version use the following directive instead. 
# RateReadBPS 20000
```

Ubuntus proftp uses the "TransferRate" 

Btw. Thanks for the trickle advice.. How do i start a server with trickle can i somehow do a 
```
sudo trikle -d 20 -u 10 /etc/init.d/proftpd start
```?

---

### Post by 23meg on 2005-12-23
You just append trickle and its parameters as a prefix to whatever you want to limit. Not sure if it will handle a script with an option correctly though, but it wouldn't hurt to try.

---

### Post by otey on 2005-12-24
Hmm.. tried it now.. Not working. No limit when running proftp width "sudo trickle -d 2 -u 1 /etc/init.d/proftpd start"

But that dont matter.. I figure its more for programs and not servers..
plus i use transerrate now.. Works fine

Thanks for the replies 23meg.

---

### Post by 23meg on 2005-12-24
You're welcome; it seems this version of trickle is quite CPU hungry (bug?) anyway and is best used with attention.

---

