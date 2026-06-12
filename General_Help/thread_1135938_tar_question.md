---
title: "tar question"
date: 2009-04-24
forum: General Help
---

### Post by tanha on 2009-04-24
I have a crontab entry that backs up a folder. I want to be able to just add anything that is new or changed to that tarball but the u and r options don't work. 

These are the commands that I've tried...

tar cvzf folder.tar.gz folder/ (the original tar) 

tar fvzr folder.tar.gz folder/ (the attempt to update the tar)
tar ufvz folder.tar.gz folder/


I get an error "tar: Cannot update compressed archives" But I can do this action in nautilus using file-roller.

---

### Post by dcstar on 2009-04-24
> **tanha said:**
> I have a crontab entry that backs up a folder. I want to be able to just add anything that is new or changed to that tarball but the u and r options don't work. 

These are the commands that I've tried...

tar cvzf folder.tar.gz folder/ (the original tar) 

tar fvzr folder.tar.gz folder/ (the attempt to update the tar)
tar ufvz folder.tar.gz folder/


I get an error "tar: Cannot update compressed archives" But I can do this action in nautilus using file-roller.

Cron jobs run in a different environment to user jobs, tell us the **exact **commands you are using.

---

### Post by tanha on 2009-04-25
> **dcstar said:**
> Cron jobs run in a different environment to user jobs, tell us the **exact **commands you are using.

As seen in original post.

---

### Post by ddrichardson on 2009-04-25
File-roller is uncompressing it, adding and re-compressing. If space is not a major issue then```
tar uvf folder.tar /folder
```
If it is then add a script to uncompress, add then compress again.

---

### Post by ddrichardson on 2009-04-25
```
#!/bin/sh
gunzip folder.tar.gz
tar uvf folder.tar.gz /folder
gzip folder.tar
```Should do it, unless someone has a better solution. Save it as backup.sh or whatever and call it as a cron job.

---

### Post by tanha on 2009-04-25
> **ddrichardson said:**
> File-roller is uncompressing it, adding and re-compressing. If space is not a major issue then```
tar uvf folder.tar /folder
```
If it is then add a script to uncompress, add then compress again.

Thanks, ddrichardson. So, I really have no way to get around this but to un-gzip and re-gzip?

---

### Post by ddrichardson on 2009-04-25
Not that I'm aware of but you never know - some bright spark might pitch up and show I'm wrong.

---

### Post by tanha on 2009-04-25
> **ddrichardson said:**
> Not that I'm aware of but you never know - some bright spark might pitch up and show I'm wrong.

:) Yes, you never know. Thank you for your help.

---

