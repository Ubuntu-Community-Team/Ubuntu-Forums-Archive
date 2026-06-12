---
title: "Bash script for ftp mirror"
date: 2011-08-04
forum: Desktop Environments
---

### Post by lucacerone on 2011-08-04
Dear all,
I recently bought an host to have a personal website
and would like to create a bash script to create
make a mirror copy of it and then add it to crontab to run once a week.

Essentially what I want to do is to get the website by using
wget -m [ftp://user:pass@ftp.host/mydir](ftp://user:pass@ftp.host/mydir)

Once this is done I'd like to have everything in an archive
called mysite.date.tar.7z

I've no experience at all of bash scripting but I guess this should be an easy task?

Can some of you help me in make the user and password not visible ?

Is there any other option better than wget? (maybe rsync it works better?)

Thanks a lot in advance to all of you,
Cheers, -luca

---

### Post by -jrosco- on 2011-08-04
Does your host run ssh service? To use rsync you would need a ssh server running . If you what to mirror over ftp use ncftp

---

### Post by lucacerone on 2011-08-05
Hi Jrosco unfortunately I have no ssh service, nor I can access through sftp.
I'll google for ncftp (I don't know what it is)
Thanks for the advice,
Cheers, Luca

---

