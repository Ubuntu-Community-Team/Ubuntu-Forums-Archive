---
title: "cron-apt, email on completion"
date: 2009-03-12
forum: General Help
---

### Post by black-mamba on 2009-03-12
I am having some trouble with my project, I'm trying to add some extra custom headers to the con-apt notification email.

I have got cron-apt to work correctly.
However I can not get it to email me, I will need to be able to do this to test any changes I make to the header.
It seems I am blocked from contacting the Gmail smtp servers, I have tried telneting to: telnet smtp.gmail.com 587 but it times out.
I'm using sendmail and ssmtp to send the results from cron-apt to my address.

I think I have the ssmtp.conf file setup for Gmail
```

# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster
 
# GMAIL configuration
mailhub=smtp.gmail.com:587
AuthUser=edward.malone88@gmail.com
AuthPass=*********
UseSTARTTLS=YES
 
# The full hostname
hostname=edward-laptop-linux

```

When I run cron-apt it completes and downloads any updates but on the onexit it gives the error.
```

edward-laptop-linux cron-apt: The following packages will be upgraded:
edward-laptop-linux cron-apt:  libpurple-bin libpurple0 pidgin pidgin-data
 edward-laptop-linux cron-apt: 4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
edward-laptop-linux cron-apt: Need to get 0B/3264kB of archives.
edward-laptop-linux cron-apt: After this operation, 0B of additional disk space will be used.
edward-laptop-linux cron-apt: Download complete and in download only mode
edward-laptop-linux /USR/SBIN/CRON[10513]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
edward-laptop-linux sSMTP[10481]: Unable to connect to "smtp.gmail.com" port 587.
edward-laptop-linux sSMTP[10481]: Cannot open smtp.gmail.com:587
edward-laptop-linux dhclient: DHCPREQUEST of 172.18.2.184 on eth0 to 172.18.0.2 port 67
edward-laptop-linux dhclient: DHCPACK of 172.18.2.184 from 172.18.0.2
edward-laptop-linux dhclient: bound to 172.18.2.184 -- renewal in 1683 seconds.

```

Thanks in advance.
Note: I am totally new to this so feel free to point out my stupidity :)
If I'm going about it totally wrong how should I do it?

---

