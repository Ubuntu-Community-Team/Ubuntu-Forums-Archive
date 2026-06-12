---
title: "rsync and comcast on-line storage"
date: 2009-01-13
forum: General Help
---

### Post by misterfixit on 2009-01-13
How to rsync from my box to comcast on-line storage?

ftp to comcast goes like this:  [ftp://upload.comcast.net](ftp://upload.comcast.net) (enter user and then password)

When I attempt this to my local box, it works fine:

rsync -arvqsPF --exclude='/.gvfs' --exclude=/home/dave/FrostWire/* /home/dave/* /media/Backup/Daily

When I attempt this from my local box to comcast:

rsync -arvqsPF  ~ftp/upload.comcast.net: "/Backup/Daily" --exclude='/.gvfs' --exclude=/home/dave/FrostWire/* /home/dave/* /media/Backup/Daily

I run into a permission problem in that I can't figure out how to input my id and pass automatically.  I've already used other ftp to set up directories on the comcast server.

advice please :-)  Thank you in advance.

---

### Post by misterfixit on 2009-01-14
Yoo- Hoo .... Bumpity-Bump-Bump ...Pretty Please?  ):P

Dave

---

### Post by SoCalChris on 2009-01-14
My guess is that their server is not set up as an rsync server, it's ftp only.

---

### Post by jerome1232 on 2009-01-14
couldn't you mount the ftp share using curlftpfs and then rsync to it?

ie
```
curlftpfs ftp.site.com /media/backup
rsync -options /source/files /media/backup
```

---

### Post by dovidhalevi on 2009-07-20
> **jerome1232 said:**
> couldn't you mount the ftp share using curlftpfs and then rsync to it?

ie
```
curlftpfs ftp.site.com /media/backup
rsync -options /source/files /media/backup
```

I have been trying this to no avail. Curl (and curl is what translates your local commands to ftp commands here) does NOT support rsync.

---

