---
title: "Set updates to download at a certain time"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Johnathon on 2006-07-20
Hello...

I'm using plus.net as a broadband provider, and you get unlimited transfer off peak, which is 0000 to 1600.

Would it be possible to set the updates in ubuntu Dapper Drake, to either download during that time, or download and install in that time?
And if so how?

I'm not that brilliant at Linux, (just starting to learn now!) so not too technical would be good. I understand, and can use the terminal, and some functions of.
I understand what you mean by a cron script, but cant make one, for example.

Any help would be appreciated!

Johnathon

---

### Post by mogelhead on 2006-07-21
Ubuntu documentation: [CronHowto]("https://help.ubuntu.com/community/CronHowto")

Minimalistic way. Warning: I have not tested it! Use at your own risk.

Edit the file with scheduled commands
```
sudo crontab -e
```

Instert "0 24 * * * apt-get update; apt-get upgrade -y" into the file.

Save

This will first fetch a list with avaliable updates, then install available updates each day at 00:00 o clock.

"apt-get upgrade" will download *and* install, but there is a -d command line parameter (from man page of apt-get): 
> -d, --download-only
Download only; package files are only retrieved, not unpacked or installed.

There are more advanced ways of doing this, logging could be nice to have for example, see these two guides from the Ubuntu documentation:
[AutoWeeklyUpdateHowTo]("https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo")
[AutomaticSecurityUpdates]("https://help.ubuntu.com/community/AutomaticSecurityUpdates")

Although both descibe weekly updates.

---

### Post by Johnathon on 2006-07-21
Thats exactly what I wanted.. thanks!

Now... all I need to do is wait till the next (hopefully fixed) kernel version comes out, and I'll start running this :)

---

