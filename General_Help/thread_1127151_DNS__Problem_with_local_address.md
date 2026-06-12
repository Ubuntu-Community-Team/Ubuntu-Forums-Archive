---
title: "DNS : Problem with local address"
date: 2009-04-16
forum: General Help
---

### Post by StuckInABox on 2009-04-16
Hi everyone,

I`ve been tasked to set up a DNS server for our office, and have NO experience whatsoever with DNS...(we are a noob company trying to set up our environment ourselves)

I installed Ubuntu 8.04 and managed to follow directions from this site about installing and configuring BIND9...aaaaaahhhhh...scary stuff..

What I am trying to achieve : 

1) Have a DNS server that can go out the office and resolve addresses to IP`s, so people can surf the web from the office.

I managed this part ok by telling resolv.conf to use an external nameserver

2) Have a DNS server that can point people in the office to a machine in the office.

For example, on a seperate server we run a web app and I want people to open their browser and type in [http://webapp.companyname.local](http://webapp.companyname.local) and the DNS must automagically send them to the box, where the web app is running.

This is part I cannot get right...and reading more DNS/BIND stuff is making my eyes bleed, and I still do not get it right.

Can I post my files here, and what ones can I post so you kind people can help me figure this out.

Thank you for your time, all assistance will be greatly appreciated

---

### Post by JochenJung on 2009-04-16
Maybe a tool like webmin could help you. Its a website frontend you can use for example to configure bind. Should make it a lot easier for you.

Install it using sudo apt-get install webmin

---

### Post by Cheesemill on 2009-04-16
Have you had a look [here]("http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/"), I think this is the tutorial I followed to set up my internal DNS and it only took a few minutes.

If your not having any luck then post the contents of your named.conf.options named.conf.local and any zone files you have and I'll take a look for you.

Cheesemill

---

### Post by StuckInABox on 2009-04-20
@JochenJung - I installed webmin but don`t notice anything different than what I have in my configs when I edit them by hand.

@Cheesemill - I uninstalled bind using apt with the --purge option and followed that tutorial you mentioned line by line. Still a no go :(

My files as requested :

named.conf:
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
                196.41.3.194;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

My named.conf file :
```
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "local.lan" IN {
        type master;
        file "/etc/bind/zones/local.lan.db";
};

zone "2.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.2.168.192.in-addr.arpa";
};

```

I set up the zones directory as suggested in the article you pointed to, and added two files in that directory :

local.lan.db :
```
local.lan. IN SOA mainserver.local.lan. hostmaster.local.lan.{
        200904204; serial
        8H ; refresh
        4H ; retry
        4W ; expire
        1D ; minimum
}

;NS indicates that mainserver is the nameserver on local.lan
local.lan. IN NS mainserver.local.lan.
;Set the address for localhost.local.lan
localhost       IN A 127.0.0.1
;Set the hostnames in alphabetical order
belkin          IN A 192.168.2.1
cradlepoint     IN A 192.168.2.10
hp2840          IN A 192.168.2.211
hp7500          IN A 192.168.2.210
mainserver      IN A 192.168.2.240
trac            IN A 192.168.2.232

```

..and rev.2.168.192.in-addr.arpa :
```

;IP to Hostname DNS pointers for 192.168.2.0 subnet
@ IN SOA mainserver.local.lan. hostmaster.local.lan.{
        2009042002 ; serial
        8H ; refresh
        4H ; retry
        4W ; expire
        1D ; minimum
}
;define the authoratative server
IN NS mainserver.local.lan.
;Hosts on the LAN
211     IN PTR hp2840.local.lan.
210     IN PTR hp7500.local.lan.
232     IN PTR trac.local.lan.

```

I restart bind9 after doing this and try to go to mainserver in my browser...it says page not found...if I type in the mainserver IP address in my browser I get the web server running on there...but it doesnt work with names.

Any ideas please...

Thank you both for replying, I appreciate your time and involvement with my problem.

StuckInaBox

---

