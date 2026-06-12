---
title: "PROFTPD can't start"
date: 2008-03-30
forum: Desktop Environments
---

### Post by jazzguitarplayer on 2008-03-30
Hello Linux freaks I have problem with Proftpd. I'm totally new to Linux, so I would appreciate you can help me out. I can't get Proftpd running and got the next error:


root@linux-computer:/etc# /etc/init.d/proftpd restart

 * Stopping ftp server proftpd                                           [ OK ] 

 * Starting ftp server proftpd                                                 
  - IPv6 getaddrinfo 'linux-computer' error: No address associated with hostname

                                                                                           [ OK ]


I read somewhere that I have to modify the /etc/hosts file and the dns record, /etc/bind/named.conf. I have running a  DNS server. I read somewhere that I have to these files. I alread did with the /etc/hosts as you can see but I don't know how to add my hostname in the /etc/bind/named.conf. If this is not the solution to my problem just let me know! 



  GNU nano 2.0.6              File: /etc/hosts                                  



127.0.0.1 localhost

192.168.1.12 linux-computer



# The following lines are desirable for IPv6 capable hosts

::1 ip6-localhost ip6-loopback

fe00::0 ip6-localnet

ff00::0 ip6-mcastprefix

ff02::1 ip6-allnodes

ff02::2 ip6-allrouters

ff02::3 ip6-allhosts

192.168.1.11 black



DNS record:



// This is the primary configuration file for the BIND DNS server named.

//

// Please read /usr/share/doc/bind9/README.Debian.gz for information on the

// structure of BIND configuration files in Debian, *BEFORE* you customize

// this configuration file.

//

// If you are just adding zones, please do that in /etc/bind/named.conf.local



include "/etc/bind/named.conf.options";



// prime the server with knowledge of the root servers

zone "." {

        type hint;

        file "/etc/bind/db.root";

};



// be authoritative for the localhost forward and reverse zones, and for

// broadcast zones as per RFC 1912



zone "localhost" {

        type master;

        file "/etc/bind/db.local";

};



zone "127.in-addr.arpa" {

        type master;

        file "/etc/bind/db.127";

};



zone "0.in-addr.arpa" {

        type master;

        file "/etc/bind/db.0";

};



zone "255.in-addr.arpa" {

        type master;

        file "/etc/bind/db.255";

};



// zone "com" { type delegation-only; };

// zone "net" { type delegation-only; };



// From the release notes:

//  Because many of our users are uncomfortable receiving undelegated answers

//  from root or top level domains, other than a few for whom that behaviour

//  has been trusted and expected for quite some length of time, we have now

//  introduced the "root-delegations-only" feature which applies delegation-only

//  logic to all top level domains, and to the root domain.  An exception list

//  should be specified, including "MUSEUM" and "DE", and any other top level

//  domains from whom undelegated responses are expected and trusted.

---

### Post by jazzguitarplayer on 2008-03-30
I also add "UseIPv6 on" to /etc/proftpd.conf. but it didn't solve the problem. :(

---

