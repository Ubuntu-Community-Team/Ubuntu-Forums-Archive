---
title: "dpkg: parse error, in file `/var/lib/dpkg/available' near line 1029 package `wine-ge"
date: 2009-05-26
forum: Desktop Environments
---

### Post by nanderv on 2009-05-26
[COLOR=#662222]I do not know what went wrong, but suddenly I could n't run ubuntu in graphical display. I solved this problem with: sudo dpkg-reconfigure xserver-xorg . Afterwards it worked well again, but when i shut Ubuntu down and restarted... I wasn't able to install any software anymore... this is an example of what's happening:

administrator@halley:~$ sudo apt-get install wine
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
administrator@halley:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following packages will be upgraded:
  wine
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 8340kB of archives.
After this operation, 119kB of additional disk space will be used.
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main wine 1.1.22~winehq0~ubuntu~9.04-0ubuntu1 [8340kB]
Fetched 8340kB in 13s (599kB/s)                                   
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1029 package `wine-gecko':
 field name `[' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

Is there a solution for this problem? I have wine 1.1.21 installed, but I would like to update to 1.1.22.
[/COLOR]

---

### Post by nanderv on 2009-05-26
I found the solution myself. If you are having the same problems, click [here]("https://answers.launchpad.net/ubuntu/+question/10265").

---

