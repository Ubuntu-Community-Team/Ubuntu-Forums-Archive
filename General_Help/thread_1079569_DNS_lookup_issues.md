---
title: "DNS lookup issues"
date: 2009-02-24
forum: General Help
---

### Post by fozzyuw on 2009-02-24
Hi all and thanks in advance to the community.

I'll start by admitting I'm a fairly green Linux newbie.

Here's my situation.  I've got a Linux box (currently 8.04 LTS) and at some point I've setup reverse DNS lookup on it.  However, I'm do not recall when or how I did it.  It was a while ago and a lot of the time was spent with me following (or trying to follow) various tutorials on setting up a Linux server (for websites).

Here's what I do know.  Logging in via putty or WinSCP would take several seconds between the login name prompt to get the password prompt.

I was talking to our firewall guy and he mentioned that this server is going out to DNS IP to do a reverse lookup, which is why it's taking so long.  I also have a feeling the IP addresses used are invalid.

This is causing a timeout and hence, why it's taking so long.  I did discover that in the SSH config, that if I add the line
```
UseDNS no
```
Solved the issue of DNS lookups for SSH, but I'm still having an issue with finding what's fully causing these DNS lookups.

The main issue being that I can't do...
```
sudo apt-get update
sudo apt-get upgrade
```
because the system is hanging and our Firwall guy said the server is performing the DNS lookup but not getting a response.

So, any ideas of what setting I changed to cause these DNS lookups so I can find the configuration and turn it off?

Cheers!
Fozzy

---

### Post by fozzyuw on 2009-02-24
Alright,

looks like I figured it out.  I had to change my settings in...

/etc/resolv.conf

That's where the DNS was set and causing problems.

---

