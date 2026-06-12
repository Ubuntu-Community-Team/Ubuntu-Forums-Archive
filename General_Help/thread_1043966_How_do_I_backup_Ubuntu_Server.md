---
title: "How do I backup Ubuntu Server?"
date: 2009-01-19
forum: General Help
---

### Post by mishathegoat on 2009-01-19
Hey everyone,
I recently installed Ubuntu Server 8.10 on a home-made server. I'm always making changes and testing things.. screwing things ups.. and usually end up having to install Ubuntu from scratch, losing all my settings and junk.

Is there a quick and easy way to backup everything, and easily restore it if I screw something up?

Thanks,
Misha

---

### Post by cariboo on 2009-01-19
I just found a cool app called mybashburn. It is a command line cd burning application. It is available in the repositories. To install it, at the prompt type:

```
sudo apt-get install mybashburn
```

You can now burn your configuration files to a cdrom and then when you need the configuration files you have them on cd.

Personally,  I have a seperate /home partition, and if I have to reinstall, I first copy the whole /etc directory to my home partition, then after installation I just copy the configuration files I need back to /etc.

Jim

---

### Post by AJExtreme on 2009-01-19
Just the same as I am trying to figure out.

You need to create seperate partitions for the data and users from the os... 

I am working on figuring some of this out but not on the extent of having a server.

Dont know if this will help you any, with your problems but worth a shot...

[http://ubuntuforums.org/showthread.php?t=1043881](http://ubuntuforums.org/showthread.php?t=1043881)

---

### Post by DJonsson2008 on 2009-01-19
I need to deal with this soon, but have learned some basics recently
working with workstations.

First it seems the new machine must match the version installed on
the old machine, including all updates.

Then...

Doesn't backing/restoring up /etc and /home accomplish the primary
objective of moving the mass of settings over.

It seems this can be done simply by copying all the files to any drive, usb flash stick, cd rom and restoring from there.

---

### Post by mishathegoat on 2009-01-19
> **DJonsson2008 said:**
> I need to deal with this soon, but have learned some basics recently
working with workstations.

First it seems the new machine must match the version installed on
the old machine, including all updates.

Then...

Doesn't backing/restoring up /etc and /home accomplish the primary
objective of moving the mass of settings over.

It seems this can be done simply by copying all the files to any drive, usb flash stick, cd rom and restoring from there.

Hmmm.. I'm pretty sure I would need to back up more than just the /etc and /home directory.. Maybe I'm wrong?

---

### Post by hyper_ch on 2009-01-19
maybe also /var/www and /var/lib/mysql but mysql dbs shouldn't not be backupped that way... then you might also want to back the list of install packages...

---

