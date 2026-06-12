---
title: "Repetative process.."
date: 2006-03-07
forum: Desktop Environments
---

### Post by fieldyweb on 2006-03-07
I have setup a macro called updns and i would like this macro to run once every five minutes..

Basically my /etc/resolv.conf keeps resetting back to nameserver 192.168.1.1 ans i want it to actually have the routers DNS entry in the file /etc/resolv.conf..

however the dhcp demon somewhere alnong the line keeps resetting the file back to "default"

I tried editing various files here, and nothing seems to help, and i have contacted dlink who are next to useless.. so for the time being if i could find a way to run the command i have created via a macro every 5 mins that would solve the problem...

---

### Post by cwaldbieser on 2006-03-07
[QUOTE=fieldyweb]I have setup a macro called updns and i would like this macro to run once every five minutes..

Basically my /etc/resolv.conf keeps resetting back to nameserver 192.168.1.1 ans i want it to actually have the routers DNS entry in the file /etc/resolv.conf..

however the dhcp demon somewhere alnong the line keeps resetting the file back to "default"

I tried editing various files here, and nothing seems to help, and i have contacted dlink who are next to useless.. so for the time being if i could find a way to run the command i have created via a macro every 5 mins that would solve the problem...[/QUOTE]

You could create a cron job.  kcron is a nice front end in kubuntu.  Not sure about a front end in Ubuntu, but you could always just make a crontab entry.

---

### Post by lamego on 2006-03-08
You don't need to setup a job for this.
You only need to disable the dhcp client from getting the dns servers:
> sudo gedit /etc/dhcp3/dhclient.conf
remove the "domain-name-servers" from the request list.

---

