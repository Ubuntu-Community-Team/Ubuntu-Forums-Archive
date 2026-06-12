---
title: "can't sync over ftp with rsync"
date: 2009-02-07
forum: General Help
---

### Post by castawaybcn on 2009-02-07
Hi there,

I am trying to sync some local files to a shared host ftp account (bluehost). Here is what I am trying (everything is in a .sh file):

1. I mount the ftp location with curlftps
```
curlftpfs -o user=myusernamec@mydomain.com:mypassword ftp://ftp.mydomain.com ~/ftp_backups

```
so far so good (I think)

2. I then try to sync the files
```
rsync -a -r --no-o --no-g --safe-links --exclude=mkstemp --progress /somefolder ~/ftp_backups/someotherfolder/
```

and it all goes bonkers in the form of this error:
> rsync: mkstemp "/someotherfolder/.prova.txt.2NZFm5" failed: Operation not supported (95)

I believe this has something to do with all files in the ftp mount being owned by root instead of my user, but at this point I don't know what to do. I tried many options and managed to get rid of a previous chgrp error, but I couldn't find anything related to this after a few hours of research.

Any help will be greatly appreciated.

---

### Post by dcstar on 2009-02-08
> **castawaybcn said:**
> Hi there,

I am trying to sync some local files to a shared host ftp account (bluehost). Here is what I am trying (everything is in a .sh file):
......
Any help will be greatly appreciated.

FTP is a stand-alone protocol, as is RSYNC.

The only commands you can run in an FTP session are FTP commands.

---

### Post by hyper_ch on 2009-02-08
you don't have shell access? it would make it mcuh simpler then for rsycn :(

---

### Post by castawaybcn on 2009-02-08
thanks for answering, and sorry for the delay in getting back to you (sleeping time where I live)

@dcstar
sure, but I am running them from a bash script, and they do work the other way around in a different server (that one runs windows).

@hyper_ch
nope, ssh is only reserved to the root ftp account, and so far I cannot use it

Any ideas where I should be looking at? so that at least I can do more research and bother you again ;)

---

### Post by hyper_ch on 2009-02-08
I never tried any syncing over ftp so I have no clue.

---

### Post by castawaybcn on 2009-02-08
are there other alternatives for syncing other than rsync? I tried unison (requires ssh) and conduit (way too basic)

---

### Post by hyper_ch on 2009-02-08
some ftp programs have a sync feature... filezilla might be one of them.

---

### Post by castawaybcn on 2009-02-08
tx, will give that a try. Although I was hoping for something I could script and automate...

---

