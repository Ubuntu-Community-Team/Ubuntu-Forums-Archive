---
title: "apt-get install"
date: 2009-01-19
forum: General Help
---

### Post by supernova1 on 2009-01-19
When I use apt-get install to install software It always starts out around 700kb/s and then gets down to around 4kb/s after a few seconds.  I have downloaded many large files via http through my web browser and also via ftp, I may get some slow down after a few seconds, but the download usually stays around 300kb/s, is this normal for apt-get, is it the servers I am downloading from?  This happens every time, so downloads can sometimes take all day.

Thanks,

David

---

### Post by DizzyEwok on 2009-01-19
It must be to do with your internet, im not an expert, but could your NAT type affect it?

---

### Post by albinootje on 2009-01-19
> **supernova1 said:**
> When I use apt-get install to install software It always starts out around 700kb/s and then gets down to around 4kb/s after a few seconds.  I have downloaded many large files via http through my web browser and also via ftp, I may get some slow down after a few seconds, but the download usually stays around 300kb/s, is this normal for apt-get, is it the servers I am downloading from?  This happens every time, so downloads can sometimes take all day.


There are quite some mirrors to choose from (except for security.ubuntu.com), are you using a mirror close to you ?
Try another one which is also not that far away.
You would do this with
```

sudo gedit /etc/apt/sources.list

```

For example :
uk.archive.ubuntu.com vs. de.archive.ubuntu.com vs. fr.archive.ubuntu.com vs. ch.archive.ubuntu.com etc.

---

