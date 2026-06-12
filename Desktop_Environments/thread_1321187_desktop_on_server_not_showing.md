---
title: "desktop on server not showing"
date: 2009-11-09
forum: Desktop Environments
---

### Post by nomad27 on 2009-11-09
Greetings, I believe my desktop issue is related to the vga drivers, but just wanted to get a second opinion before I start figuring out how to compile them. Last night I installed 9.10 server..first time doing this, all went great! I then thought it would be cool to have a desktop so I used:
```

sudo aptitude update
sudo aptitude install ubuntu-desktop
then
sudo /etc/init.d/gdm start

```Basically, on startup, I get a small white ubuntu logo, but then an error flashes quickly (very quickly) on the bottom saying something along the lines of "one or more of the mounts in fstab cannot be mounted"..and the screen goes black, also unable to log on via webmin on network, so I have to kill the power. On restart, in recovery, I select 'repair broken package' which will then download something and go through a process, from there I can loggon remotely to webmin (no desktop on server pc, just command prompts). But again on restart, I will have the same desktop problems. 
I'm using an older gateway, with mobo 4000827, intel 845GL and have found this thread:
[http://ubuntuforums.org/showthread.php?t=30235&page=2](http://ubuntuforums.org/showthread.php?t=30235&page=2)
Again, just looking for a second opinion as to whether it is driver issues, or something else before I start messing with the drivers.
Thanks

---

