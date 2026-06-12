---
title: "'respawning too fast' error in syslog"
date: 2006-09-08
forum: Desktop Environments
---

### Post by meekish on 2006-09-08
I'm not sure this is the right forum for this thread. Mods, please feel free to move it to the correct one ;) 

I am setting up Ubuntu server in a VPS. I am tailing my syslog to keep track of my server's condition, and am getting a ton of these:

```
Sep  8 05:28:35 reformationstudios init: Id "3" respawning too fast: disabled for 5 minutes
Sep  8 05:28:35 reformationstudios init: Id "5" respawning too fast: disabled for 5 minutes
Sep  8 05:28:35 reformationstudios init: Id "4" respawning too fast: disabled for 5 minutes
Sep  8 05:28:35 reformationstudios init: Id "6" respawning too fast: disabled for 5 minutes
Sep  8 05:35:16 reformationstudios init: Id "1" respawning too fast: disabled for 5 minutes
Sep  8 05:35:16 reformationstudios init: Id "5" respawning too fast: disabled for 5 minutes
Sep  8 05:35:16 reformationstudios init: Id "3" respawning too fast: disabled for 5 minutes
Sep  8 05:35:16 reformationstudios init: Id "6" respawning too fast: disabled for 5 minutes
Sep  8 05:35:16 reformationstudios init: Id "4" respawning too fast: disabled for 5 minutes
Sep  8 05:35:16 reformationstudios init: Id "2" respawning too fast: disabled for 5 minutes
```

I have no idea what these messages mean, if I should be worried about them, or where I might possibly start to begin troubleshooting them. Any ideas?

---

### Post by gruepig on 2006-09-08
> **meekish said:**
> I have no idea what these messages mean, if I should be worried about them, or where I might possibly start to begin troubleshooting them. Any ideas?

Well, init is the "master" parent process on a Linux system.  It's responsible for spawning lots of other processes.  These run out of /etc/inittab.

I'd guess you need to comment out the getty lines 1-6 in /etc/inittab and then 'kill -HUP 1' to restart init.

A google search for "VPS inittab respawn ubuntu" confirms and has some other notes:
[http://wiki.vpslink.com/index.php?title=Ubuntu_notes](http://wiki.vpslink.com/index.php?title=Ubuntu_notes)

---

### Post by bernie667 on 2006-10-15
Hi!
I had the problem too at a friends AMD machine.
When we tried to 'start and install ubuntu' it stopped when setting up drivers or so... 
what then happens is known:
... INIT: respawning too fast ....
checking the CD-ROM for errors revealed that there was an error on the CD!
the CD was burned again, but that didn't help.

the problem was solved by simply downloading the iso image again (not from this site:
[http://ftp.ds.karen.hj.se/pub/os/linux/ubuntu-iso/dapper/](http://ftp.ds.karen.hj.se/pub/os/linux/ubuntu-iso/dapper/)
)
and then it worked.
So it's not always the machines fault, but it could also be the CD!

---

