---
title: "DNS values resetting in Network Config"
date: 2006-07-11
forum: Desktop Environments
---

### Post by xpmaniac4ever on 2006-07-11
Every time after rebooting my Ubuntu Dapper 6.06 system, the values for the DNS servers that I have set in network configuration get resetted. I set three DNS servers and after restart I have none !! At the beginning I thought it was a Xubuntu issue, but then I formatted and reinstalled with Ubuntu and after 3 days of usage the same issue appeared. Can anyone help ?

---

### Post by xpmaniac4ever on 2006-07-11
Anyone ? Please ?

---

### Post by tom56 on 2006-07-11
This has just started happening to me. I'm not sure what set it off: it was either an update or installing kde (which I have now removed, though the problem persists). Not found a fix yet.

---

### Post by xpmaniac4ever on 2006-07-11
MUST BE FIXED IN EDGY ! Can anyone provide a quick fix for this ?

---

### Post by testube_babies on 2006-07-11
This has been a problem since the first Ubuntu release.  Each time a new version is released, I'm hoping it's fixed but am always disappointed.  It's the only thing that REALLY REALLY bothers me.

---

### Post by fifth on 2006-09-18
> **testube_babies said:**
> This has been a problem since the first Ubuntu release.  Each time a new version is released, I'm hoping it's fixed but am always disappointed.  It's the only thing that REALLY REALLY bothers me.

I've only recently started having this problem on edgy - dapper and previous worked perfectly.But now, 9 out of 10 reboots will wipe the dns settings and edgy will not find alternative settings from the router, ie i end up not being able to resolve any domains.

[QUOTE=tom56]I'm not sure what set it off: it was either an update or installing kde[/QUOTE]

Strangely, i also recently installed the kde desktop (although decided not to use it, but still installed). Not sure why this could cause the problem, maybe just coincidence with the above post.

Any advise to fix would be *very* much appreciated - esp when the wife uses the laptop and complains about firefox not working ;).

Is there a quick script which could be run when logging in to set the dns entries?

---

### Post by knitwit on 2006-09-18
For me editing /etc/dhcp3/dhclient.conf to include the line:

prepend domain-name-servers 195.92.195.94;

was the solution. I think this usage requires DHCP to work. On some systems the config file is found at /etc/dhcp/dhclient.conf

---

