---
title: "hostname -&gt; gethostbyname() Doesn't. No ADMIN ability"
date: 2007-03-16
forum: Desktop Environments
---

### Post by johnbl on 2007-03-16
At some point - and I suspect it was mucking about with the notebook in an aircraft... Mouse has a mind of its own in a moving vehicle I found, hostname was corrupted.

Booted in recovery and entered hostname interserve3
and hostname retunred interserve3.
Rebooted - and tested.

sudo: unable to lookup interserve3 via gethostbyname()

So no change there.

Command line instructions help seem to suggest hostname = domainname and both can be set from a file.

Has anyone come across this situation and recovered short of a reinastall?

Any ideas most welcome.

John:confused:

---

### Post by taurus on 2007-03-16
Both /etc/hostname and /etc/hosts need to use the same name or sudo won't work and network won't work, either.  Therefore, boot into recovery mode from GRUB menu and edit those two files.

```
nano /etc/hostname
nano /etc/hosts
```
Save and each for each file with <Ctrl>o and <Ctrl>x.

And if you are not sure what to do, post both of them here.

---

### Post by johnbl on 2007-03-17
Thanks for that.
nano worked ok - never heard of that one, there simply MUST be a book somewhere with all this good stuff in it on Ubuntu!.

hostname didn't exists so a new file written containing my old system name only.
hosts was in existance. Contained 
127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I inserted below
127.0.0.1 localhost.localdomains localhosts

interserve3

and saved it.

booted Ctrl+D
and tested in a terminal window

john@:~$ sudo
sudo: unable to lookup  via gethostbyname()
john@:~$

So zip change.

 I assume the localhost.localdomain localhost is the equivalent of tying localhost = local domain 
 so rather than inserting a line below that statement should I insert it before OR replace anything in the declaration..?
or create a file called localhosts..?

Sorry to be such a clutz <sigh>

Johnbl

---

