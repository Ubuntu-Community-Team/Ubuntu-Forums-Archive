---
title: "Help with backups"
date: 2009-04-13
forum: General Help
---

### Post by wgarider on 2009-04-13
I have tried several backup solutions - sbackup, backerupper and a few scripted solutions - just haven't found one that I really liked. 

I was hoping for something that I could just backup the default dirs, like sbackup does, but none of them seeem to work for me. sbackup, in particluar, I could never open the tar.gz it creates. Is there an issue backing up to a USB drive?

What does everyone do to backup there systems? Any suggestions would be great. Thanks

---

### Post by RedSingularity on 2009-04-13
I use Clonezilla.  Works perfectly for me!

---

### Post by cybergalvez on 2009-04-13
I use Back in time and just back up my personal stuff

---

### Post by wgarider on 2009-04-14
> **Shadow121 said:**
> I use Clonezilla.  Works perfectly for me!

Thanks - I'll take a look!

---

### Post by wgarider on 2009-04-14
> **cybergalvez said:**
> I use Back in time and just back up my personal stuff

Thanks - this may be a good fit. I'll take a look.

---

### Post by Seventh Reign on 2009-04-16
I'd like to hear some opinions of Back In Time.  I've been using it for about 3 days, and so far It seems to be everything I wanted .. but has anyone used it to actually restore?

---

### Post by ushills on 2009-04-16
If you dont mind paying a small sum look at jungledisk it uses Amazon S3 servers for off-site backup (really small storage charge) or duplicity that also uses S3 but from CLI only.

---

### Post by halok on 2009-04-16
```
rsync -av (source) (target)
```

then every now and then i go

```
rsync -av --del (source) (target)
```

to clean up the old files, works a treat.:D

---

### Post by Xiangxianni on 2009-04-16
> **halok said:**
> ```
rsync -av (source) (target)
```

then every now and then i go

```
rsync -av --del (source) (target)
```

to clean up the old files, works a treat.:D

Great ideas,we can add it to cron jobs.

---

### Post by halok on 2009-04-16
> **Xiangxianni said:**
> Great ideas,we can add it to cron jobs.

Thats exactly what i do. :)

---

### Post by asadqamber on 2009-07-09
I am trying to configure jungledisk through the CLI, but I am having trouble with the config. How did you manage through the CLI.

---

### Post by asadqamber on 2009-07-09
> **ushills said:**
> If you dont mind paying a small sum look at jungledisk it uses Amazon S3 servers for off-site backup (really small storage charge) or duplicity that also uses S3 but from CLI only.


I am trying to configure JungleDisk CLI to make and retrieve a backup, but I am having trouble with the config. How did you manage? I read posts and the install document, but I just can't find the config file.

---

