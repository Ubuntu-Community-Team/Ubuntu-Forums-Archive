---
title: "How do I disable these?"
date: 2006-04-11
forum: Desktop Environments
---

### Post by ardchoille on 2006-04-11
I am running Ubuntu Dapper Drake flight 6. When I boot and log into gnome, I notice several services that are running, services which I will likely never use (I don't own a printer or bluetooth devices nor do I use bittorrent). I can turn them off with the below commands:

```

sudo /etc/init.d/bittorrent stop
sudo /etc/init.d/bluez-utils stop
sudo /etc/init.d/cupsys stop
sudo /etc/init.d/hplip stop

```

There are likely other services in there which I'll never use but don't know how to find out what they are.

However, my question is, how do I properly disable them from starting in the first place?

I have noticed that there are symlinks in /etc/rcx.d (where x is 1 - 6) that are linked to these services in /etc/init.d. Are these symlinks in /etc/rcx.d for the various runlevels?

---

### Post by Ramses de Norre on 2006-04-11
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
Be careful on turning off services, it can break your system.

And those symlinks are indeed for the various runlevels.

---

### Post by art on 2006-04-12
As Ramses said, but in order to have a backup of what was before here is place to look, along with explanation of what some services do:

[http://ubuntuforums.org/showthread.php?t=89491&highlight=reduce+boot+time](http://ubuntuforums.org/showthread.php?t=89491&highlight=reduce+boot+time)

---

### Post by ardchoille on 2006-04-12
[QUOTE=Ramses de Norre]sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
Be careful on turning off services, it can break your system.

And those symlinks are indeed for the various runlevels.[/QUOTE]
Thank you very much. That is a very nice app and I have been looking for something like that ever since I switched to Ubuntu.

---

### Post by ardchoille on 2006-04-12
[QUOTE=art]As Ramses said, but in order to have a backup of what was before here is place to look, along with explanation of what some services do:

[http://ubuntuforums.org/showthread.php?t=89491&highlight=reduce+boot+time](http://ubuntuforums.org/showthread.php?t=89491&highlight=reduce+boot+time)[/QUOTE]
You know, I was tempted to remove the symlinks for runlevel 5 but I stopped myself and waited to learn the proper way to do it. Thank you for the advice and the URL :)

---

