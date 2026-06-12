---
title: "aliasing troubles"
date: 2009-04-01
forum: General Help
---

### Post by Oblivion_4 on 2009-04-01
Hi there,
I'm having troubles setting up an alias  in bash that does three things as shown below

```
#check for updates -> update -> prelink libraries
alias lolUpdate='sudo apt-get update; sudo apt-get dist-upgrade; sudo
/etc/cron.daily/prelink'

```

ok now the next box below gives me permission denied when I try to pre-link my libraries with the third step. The first few lines of code are from the command 'sudo apt-get dist-upgrade'

```
Do you want to continue [Y/n]? y
Setting up etcinsvk (1.0) ...
dpkg: error processing etcinsvk (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 etcinsvk
E: Sub-process /usr/bin/dpkg returned an error code (1)
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
/etc/cron.daily/prelink: line 42: /var/lib/misc/prelink.quick: Permission denied
/etc/cron.daily/prelink: line 51: /var/log/prelink.log: Permission denied
/etc/cron.daily/prelink: line 52: /var/log/prelink.log: Permission denied
/etc/cron.daily/prelink: line 53: /var/log/prelink.log: Permission denied

```

What should I do to get my alias to work?

---

