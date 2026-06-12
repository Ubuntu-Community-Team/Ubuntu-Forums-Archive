---
title: "dns reset"
date: 2006-08-24
forum: Desktop Environments
---

### Post by davebradford on 2006-08-24
for some reason every 20 mins or whenever i restart the computer my dns settings get reset back to 192.168.1.1, i am refering to the ones in resolv.conf. Anybody know how i can stop this from changing and save my dns settings.

cheers..

---

### Post by NetworkGuy on 2006-08-24
Are you using DHCP?

DHCP will reset your settings everytime you restart.

---

### Post by defeca on 2006-08-24
You can edit your resolv.conf and put the dns you want to use, like this example:

nameserver 213.94.190.194
nameserver 213.94.190.236

And then you lock it with 
$ sudo chattr +i /etc/resolv.conf
To unlock (if you want to change the dns) you use:
$ sudo chattr -i /etc/resolv.conf"

---

### Post by skcoyote on 2006-08-24
> **defeca said:**
> You can edit your resolv.conf and put the dns you want to use, like this example:

nameserver 213.94.190.194
nameserver 213.94.190.236

And then you lock it with 
$ sudo chattr +i /etc/resolv.conf
To unlock (if you want to change the dns) you use:
$ sudo chattr -i /etc/resolv.conf"
If the OP is indeed using DHCP (very likely, based on the description), there's a more appropriate way to override settings by dhclient. resolv.conf is legitimately overwritten by dhclient, but you can easily control what it writes. See dhclient.conf(5) ("man 5 dhclient.conf"), and /etc/dhcp3/dhclient.conf

Particularly, you can use prepend domain-name-servers or supersede domain-name-servers options to add to or replace the name servers provided in the DHCP offer. Also useful is prepend domain-name.

You'd want something like this:

```

prepend domain-name "example.com example.net";
prepend domain-name-servers 127.0.0.1;

```

---

### Post by davebradford on 2006-10-09
i have solved this problem, in the end i just made resolv.conf a read-only file!! magic!!

---

### Post by makeshift on 2006-10-10
Well, I find skcoyote's solution to be more elegant ;). Thanks to this thread, I've solved my DNS-overwrite-problem
 [http://www.ubuntuforums.org/showthread.php?t=128254&page=2]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2") -> post #13.
 
   Followed option 3 as in the code sample above and voila, my preferred dns servers are on the top of the list in resolv.conf even after network restart/reboot.

---

### Post by HolyJoe on 2006-11-15
> **defeca said:**
> You can edit your resolv.conf and put the dns you want to use, like this example:

nameserver 213.94.190.194
nameserver 213.94.190.236

And then you lock it with 
$ sudo chattr +i /etc/resolv.conf
To unlock (if you want to change the dns) you use:
$ sudo chattr -i /etc/resolv.conf"

That's great!
Thanks.

---

### Post by tpf80 on 2006-12-07
I had this same issue but it even happened when I had a statid IP address. For some reason no matter what I did, my DNS would revert to 192.168.1.1 after every boot up or any time my connection was interrupted or I activated my wireless. The above example worked perfect for me:

> **skcoyote said:**
> 
```

/etc/dhcp3/dhclient.conf
prepend domain-name "example.com example.net";
prepend domain-name-servers 127.0.0.1;

```

Basically you just put the DNS server(s) you want to use in the prepend, and it will appear first in the list no matter what. If you want to add  more servers just add another line.

So 192.168.1.1 seems to appear in my DNS list still every so often, but my real dns servers are first, so it never has a problem.

---

