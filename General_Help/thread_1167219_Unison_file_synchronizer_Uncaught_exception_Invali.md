---
title: "Unison file synchronizer: Uncaught exception Invalid_argument(&quot;String.create&quot;)"
date: 2009-05-22
forum: General Help
---

### Post by uhcafigdc on 2009-05-22
unison version 2.27.57 on both server and client
kernel 2.6.26-1-686 on server
kernel 2.6.9-78.0.1 on client

I have two .prf files for syncing two sets of directories between the two computers jobs.prf and books.prf. They are almost exactly the same. 
```
#books.prf
root = /home/books
root = ssh://192.168.1.13//home/books
prefer = /home/books
batch = true
rsync = true
times = true
group = true
owner = true
retry = 2
ignore = Name *.mp3
ignore = Name *.wma
ignore = Name *.mpeg
ignore = Name *.mpg
ignore = Name *.wmv
ignore = Name *.avi
ignore = Name *.wav
backuplocation = central
backupdir = /home/user/unisonbackup/books
backup = Name *
backupprefix = $VERSION.
maxbackups = 2
logfile = /var/log/unison.books
log = true
```

```
#jobs.prf
root = /home/jobs/jobs
root = ssh://192.168.1.13//mnt/jobs/jobs
prefer = /home/jobs/jobs
batch = true
rsync = true
times = true
group = true
owner = true
retry = 2
ignore = Name *.mp3
ignore = Name *.wma
ignore = Name *.mpeg
ignore = Name *.mpg
ignore = Name *.wmv
ignore = Name *.avi
ignore = Name *.wav
backuplocation = central
backupdir = /home/user/unisonbackup/jobs
backup = Name *
backupprefix = $VERSION.
maxbackups = 2
logfile = /var/log/unison.jobs
log = true
```


books.prf runs just fine.
jobs.prf gets through with scanning local files and stops with an output looks like this
```
scanning file1234
scanning file2345
Waiting for changes from server
Uncaught exception Invalid_argument("String.create")
```


I tried adding the line `xferbycopying = false` to jobs.prf

I have tried removing the archive files from the .unison directory

I read on this Unison FAQ that there are problems when syncing new empty directories. There aren't any that I know of, and creating empty directories does not cause unison to fail like this when syncing books.prf

I ran unison -debug all jobs.prf and these are the last few lines of output
```
[server: pred] ignore 'x-title.dwg' = false
[server: update] buildUpdate: /mnt/jobs/jobs/x-title.dwg
[server: update]   buildUpdate -> Updated file
[server: xferhint] insertEntry: fspath=/mnt/jobs/jobs, path=x-title.dwg, fp=(ca5d1ae882aa9cf77d797fb5111b8c4e,)
[server: update] Setting archive for //files//mnt/jobs/jobs
Uncaught exception Invalid_argument("String.create")
<>!<>!<>!<>!aip3:/home/user#
```

It looks like it is failing on creating the archive file. The .unison directory does not contain an archive file for jobs.prf after this exit. There are archive files in the .unison directory for books.prf, which runs successfully.

---

