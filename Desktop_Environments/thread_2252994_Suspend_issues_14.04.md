---
title: "Suspend issues 14.04"
date: 2014-11-16
forum: Desktop Environments
---

### Post by cody17 on 2014-11-16
My system is set to suspend @ 15 minutes in Power Manager, but when this threshold is met the computer only goes to the lock screen. I have Googled the issue and this seems to be an uncommon bug...

I have 5 gigs of swap space.

I do receive a "Power Manager not Authorized" popup after 15 mins though,

Here is the results in dmesg: [http://pastebin.com/3dBf3iLg](http://pastebin.com/3dBf3iLg)

---

### Post by pqwoerituytrueiwoq on 2014-11-16
are you sure you set the system to suspend and not just the monitor?
does suspend on lid close work, assuming you have a laptop?

---

### Post by cody17 on 2014-11-16
I'm using a PC. Here is a screenshot of my settings:
[http://imgur.com/7iWCmEQ](http://imgur.com/7iWCmEQ)
[IMG]http://imgur.com/7iWCmEQ[/IMG]

---

### Post by pqwoerituytrueiwoq on 2014-11-19
sorry for the late reply, but i was a little too lazy to wait 15min to test the feature
works just fine for me, not sure how accurate the timer is, but i checked it over 40 min later and it was in suspend
what ever your issue is i think it is hardware specific
```
~$ apt-cache policy xfce4-power-manager;lsb_release -a
xfce4-power-manager:
  Installed: 1.2.0-4ubuntu1
  Candidate: 1.2.0-4ubuntu1
  Version table:
 *** 1.2.0-4ubuntu1 0
        100 /var/lib/dpkg/status
     1.2.0-3ubuntu4.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
     1.2.0-3ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

---

### Post by Steve DL on 2014-11-20
Hi,

You should look up (and post here) the output of the 'dmesg' command. This command pulls up messages from your kernel, and this is where things like your Linux drivers will inform you of any problems. On my laptop (running ArchLinux) I've had longstanding issues with the Ethernet driver preventing my system from sleeping, so I've had to disable it. I've also run into problems on an old Xubuntu box that were caused by a poor interaction [between Suspend and SSHFS mounts](http://www.mupuf.org/blog/2011/05/12/suspend2ram_the_init_process_and_sshfs/).

---

### Post by cody17 on 2014-11-20
[http://pastebin.com/3dBf3iLg](http://pastebin.com/3dBf3iLg)

Does this help?
Let me know if I can provide anything else useful.

Thanks

---

