---
title: "Accidentally did a &quot;sudo rm s*&quot; in /etc/init.d"
date: 2006-06-21
forum: Desktop Environments
---

### Post by prozacgod on 2006-06-21
yeah, yeah - stupid move, I accidentally did an "sudo rm s*" in /etc/init.d

I know the exact files that were removed.

pcmcia
pcmciautils
postfix
powernowd
powernowd.early
ppp
pppd-dns
procps.sh

Now is there a way to get apt to coax these files back into existance, or do I have to extract the files and restore them myself.  These files are the defaults - I never changed them.

What package do they exist in ?  Any ideas on restoring them!

Thanks in adance!

-David

---

### Post by aysiu on 2006-06-21
I have an idea, but I don't know if it'll work.

First of all... don't reboot!

Try this: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` If that doesn't work, you can try ```
sudo aptitude update
sudo aptitude install powernowd
```

---

### Post by prozacgod on 2006-06-21
Thanks, yeah I don't think a reboot in my situation would be catastrophic, but I'm not doing it nontheless.

As I suspected, updating the individual packages only checks their "known" state inside the package tree, not the broken state on the hdd, which makes sense.

What I need to do is I guess reinstall (the package), luckily I have no pcmcia, nor messed with any of those other service configuration files.

I also needed to update my desktop machine, which I've been lazily ignoring, and putting off etc, so perhaps I'll just finally update my desktop and copy the lost files - whilst I stop using my "server" as a desktop (dapper drake is nice :P)

---

### Post by aysiu on 2006-06-21
I think Synaptic has an option to reinstall packages.

---

### Post by chavo on 2006-06-21
Just in case you don't figure something out here's the p* files from my  init.d folder tarred up.

---

### Post by moffa on 2006-07-08
You can use the --reinstall command to reinstall packages
You can try ```
 sudo apt-get install --reinstall ubuntu-desktop 
```

---

