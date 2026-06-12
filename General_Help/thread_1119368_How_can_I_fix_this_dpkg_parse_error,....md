---
title: "How can I fix this: dpkg: parse error,... ?"
date: 2009-04-07
forum: General Help
---

### Post by cj00 on 2009-04-07
=> Hi, I'm confused with this, whenever I try to install something using terminal this always shows in the end:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 15632 package `console-setup':
 value for `conffiles' has malformatted line `
E: Sub-process /usr/bin/dpkg returned an error code (2)

=> also without using terminal, while installing packages this shows up:

Broken dependencies

Your system has broken dependencies. This application can not continue until this is fixed. To fix it run 'sudo synaptic' or sudo apt-get install -f' in a terminal window

=> But when I try doing that this shows up again:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 15632 package `console-setup':
 value for `conffiles' has malformatted line `
E: Sub-process /usr/bin/dpkg returned an error code (2)

=> So how do I fix this?

---

### Post by juancarlospaco on 2009-04-07
sudo apt-get clean ; sudo apt-get install -f

---

### Post by cj00 on 2009-04-07
> **juancarlospaco said:**
> sudo apt-get clean ; sudo apt-get install -f

Like I said it does'nt work, it still shows the dpkg: parse error...,

---

### Post by Snyper64 on 2009-04-18
Having the same problem but I get the following readout:```
snyper64@snyper64-desktop:~$ sudo apt-get clean ; sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2547 package `language-pack-gnome-de':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
snyper64@snyper64-desktop:~$ 
```



It seems to be a problem with "/var/lib/dpkg/available". Any ideas on how to either fix or replace this file? Its probably whats causing problems for other people too.

---

### Post by hikaricore on 2009-04-18
Looks like file corruption.
I've had similar issues in the past and have gotten around them by copying that file to a backup location (just incase).
And running:

> sudo dpkg --clear-avail
sudo apt-get update

---

### Post by Snyper64 on 2009-04-18
Thank you hikaricore, ran the commands and everything updated just fine, hopefully this will help other people with the same problem.

---

