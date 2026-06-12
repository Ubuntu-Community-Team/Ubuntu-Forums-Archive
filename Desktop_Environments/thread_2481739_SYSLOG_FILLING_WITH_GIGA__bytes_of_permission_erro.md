---
title: "SYSLOG FILLING WITH GIGA  bytes of permission error messages"
date: 2022-12-07
forum: Desktop Environments
---

### Post by pizzipie on 2022-12-07
Hi,
 
My System:
  Host: rick-Latitude-E6510 Kernel: 5.4.0-132-generic x86_64 bits: 64 
  Desktop: MATE 1.24.0 Distro: Ubuntu 20.04.5 LTS (Focal Fossa) 

My computer went nuts and the Disk Analyzer program  said I was out of space! I checked and found that the 'syslogs' were using **149 GIG**s . Looking at the logs it seems the condition has happened in the last few days.   The next-to-last file **tail_bad_syslog2.txt**, attached below, has some text about 'logrotate' which I understand controls the logs from expanding too much. After some research I emptied all the log files and got my disk space back. 

Now, after checking the 'syslog' file out it appears the same thing is happening again. See Ls -hl syslog in the next line.  

ls -hl syslog => -rw-r----- 1 syslog adm 9.3G Dec  7 16:53 syslog. 

[B]The file syslog was filled from 0 to 9.3 Gigs in less than an hour.
[/B]
The contents of that file is as follows:

Dec  7 09:14:21 rick-Latitude-E6510 org.mate.panel.applet.BriskMenuFactory[151631]: [151631:1207/091420.128250:ERROR:address_tracker_linux.cc(355)] Failed to recv from netlink socket: Permission denied (13)

[B]Repeating Endlessly !!!!!!!!!
[/B]
I don't have a clue what is going on here or how this could have happened but 'Desktop: MATE 1.24.0' must be involved.

Thanks in advance for any help in fixing this.

R

PS **Since I started this description of my problem  the 'syslog' file has gone from 9.3 gigs to 20 gigs !!!!!!!**

---

### Post by TheFu on 2022-12-08
First, set limits on the sizes that logs can reach.

```
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.

```
200M total should be 20x more than needed.

The journald.conf file controls the permanent limits.  There's a manpage for that file which explains the different options.

That will provide breathing room to research the root cause.

BTW, why is / or /var/ more than 35G?

---

### Post by pizzipie on 2022-12-09
Unfortunately none of that means anything to me and I got nowhere with it. 

However, I got looking around and intstalled MATE 1.26.0 and it seems to have stopped this behavior.

Thanks.

---

### Post by #&amp;thj^% on 2022-12-09
Something I just drove by and noticed>>>":ERROR:address_tracker_linux.cc(355)] Failed to recv from netlink socket: Permission denied (13)"
Are you using Brave Browser?

---

### Post by pizzipie on 2022-12-10
No. I use Firefox 107.0(64-bit)

Thanks for the help.

R

---

### Post by ActionParsnip on 2022-12-12
[https://bugs.launchpad.net/ubuntu/+source/brisk-menu/+bug/1879322](https://bugs.launchpad.net/ubuntu/+source/brisk-menu/+bug/1879322)

---

