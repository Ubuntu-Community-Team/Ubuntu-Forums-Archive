---
title: "partimage not in synaptic"
date: 2009-05-06
forum: General Help
---

### Post by Mirge on 2009-05-06
Anybody know where I can find partimage? Everywhere I've searched says it's in synaptic or available via apt-get... but I can't find it heh. I tried sudo apt-get install partimage too, but it's not found there either so I know I didn't overlook it in synaptic.

Please advise...

---

### Post by Mirge on 2009-05-06
Well, yet again I answer my own question...

[https://launchpad.net/ubuntu/jaunty/amd64/partimage/0.6.4-17](https://launchpad.net/ubuntu/jaunty/amd64/partimage/0.6.4-17)

For my particular application. Hope it helps.

---

### Post by kpkeerthi on 2009-05-06
Partimage is in Universe repository (System -> Administration -> Software Sources)

See: [http://packages.ubuntu.com/jaunty/partimage]("http://packages.ubuntu.com/jaunty/partimage")

---

### Post by Mirge on 2009-05-06
The only thing I see when I search for partimage is partimage-doc.

I have Universe enabled... any idea how to fix?

---

### Post by Mirge on 2009-05-06
bump.. please help.

---

### Post by Mirge on 2009-05-06
Ok well... is there a better solution for creating a full backup then?

---

### Post by Mirge on 2009-05-07
Guess not? :(

---

### Post by kpkeerthi on 2009-05-07
Check out [backup using tar]("http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a"). 

If you want to implement a quick incremental backup, use this command
```
rsync -a /home /media/Backup
```
* This will move files changed since the last backup to /media/Backup (which could be your external HDD) from /home.

If you need a graphical tool, based on rsync, check out [Back In Time]("http://backintime.le-web.org/")

All the above methods are [cron]("https://help.ubuntu.com/community/CronHowto") friendly and are easy to automate.

---

### Post by colau on 2009-05-07
> **Mirge said:**
> bump.. please help.
You can use this burning as cd.
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Mirge on 2009-05-07
> **kpkeerthi said:**
> Check out [backup using tar]("http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a"). 

If you want to implement a quick incremental backup, use this command
```
rsync -a /home /media/Backup
```* This will move files changed since the last backup to /media/Backup (which could be your external HDD) from /home.

If you need a graphical tool, based on rsync, check out [Back In Time]("http://backintime.le-web.org/")

All the above methods are [cron]("https://help.ubuntu.com/community/CronHowto") friendly and are easy to automate.

This is exactly what I was looking for. Just had to re-install Ubuntu 9.04 due to me messing around too much without knowing enough heh.

I had a bunch of junk anyway, so I'm not terribly upset with having to re-install. The import feature in the Ubuntu 9.04 installer is a life-saver... all I had to do was re-install the programs I actually used, and it retained all of my settings. I love Ubuntu.

---

### Post by Mirge on 2009-05-07
I actually couldn't get Back In Time to work, so I am making a full backup using rsync -av / /media/disk/yaddayadda now... JUST  in case :).

Thanks!

---

### Post by Mirge on 2009-05-07
Well that's odd, I ran outta space! Only using 30GB or so on this Linux install... the partition I was backing up to had 90GB free or so. Does rsync not back up only the files I specify? Or is it trying to back up the entire partition? I thought just files.. since I can see each file as it copies it.

---

