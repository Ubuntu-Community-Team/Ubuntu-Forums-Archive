---
title: "Error while setting Emblems with gvfs-set-attribute and cron"
date: 2010-08-26
forum: Desktop Environments
---

### Post by barsuk on 2010-08-26
Hi,

I already posted a link in the ubuntuusers.de Forum (german) [http://forum.ubuntuusers.de/topic/emblem-mit-gvfs-set-attribute-und-cron-setzen/]("http://forum.ubuntuusers.de/topic/emblem-mit-gvfs-set-attribute-und-cron-setzen/")

But I haven't found a solution yet. The problem is, that I wanna set an Emblem in Nautilus via a Script that is called by cron.
The problem happens in that line
```
/usr/bin/gvfs-set-attribute -t stringv /path/to/file metadata::emblems minus14
```
thats the error:
```
Error setting attribute: Setting attribute metadata::emblems not supported
```

I already tried to call the script via /etc/crontab and /var/spool/cron/crontabs/meles, i tired it with ```
/path/to/script
``` 
```
sudo -H -u meles /path/to/script
```
I already checked the $PATH Variable 
I tried it with ```
sudo -H -u meles  /usr/bin/gvfs-set-attribute -t stringv /path/to/script metadata::emblems minus14
``` directly in /etc/crontab or /var/spool/cron/crontabs/meles

Any ideas why it doesn't work? Or can anybody try if it works on your system?

Thanks!

PS Independent of cron the script works.

---

### Post by WhoSayIn on 2010-09-11
I am also getting the same error when i want to change folder's emblem. searched on google and found this page.

---

### Post by hanspr on 2010-09-20
Sets the emblem

gvfs-set-attribute -t stringv FILE_or_FOLDER metadata::emblems EMBLEM_NAME

Reads emblems set

gvfs-info -a metadata::emblems FILE_or_FOLER

Will show you what emblem is set to the file or folder

---

