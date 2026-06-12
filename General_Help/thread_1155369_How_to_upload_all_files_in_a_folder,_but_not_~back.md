---
title: "How to upload all files in a folder, but not ~backups, etc?"
date: 2009-05-10
forum: General Help
---

### Post by afowler on 2009-05-10
Hello,

1) Is there a way with sftp/scp/ftp to upload all files and folders under a directory, but to skip the ~backup, ".svn", etc. files? 

2) Is there anyway to do the same as #1 but only upload newly changed files? 

Thank you,
:)

---

### Post by Alterax on 2009-05-10
Rsync is a good one.  Here's a sample of rsync code that copies my etc directory from my laptop to my desktop over ssh:


```
rsync --compress --recursive --delete --links \
--times --perms --owner --group \
--verbose --progress --stats \
--rsh="ssh" \
--exclude "*bak" --exclude "*~" \
/etc/* 192.168.177.3:/opt/backup/laptop/etc
```

Just add --exclude statements as you deem necessary and adjust the target.  If you want to copy to a local directory just drop the IP address: portion (so in this case it would be shortened to /opt/backup/laptop/etc)

You may need to install rsync, but it's worth it.  The usage above makes an incremental backup.  It also destroys files and folders in the backup that no longer exist on the host system.  If you don't want that, remove the --delete option.

---

### Post by afowler on 2009-05-10
> **Alterax said:**
> Rsync is a good one.  Here's a sample of rsync code that copies my etc directory from my laptop to my desktop over ssh:



Thank you... I'll try rsync.


Is there an alternative that uses FTP?  I may need to use a server with just ftp access...

Thanks again,
:)

---

### Post by unutbu on 2009-05-10
I haven't used this myself, but I think the curlftpfs package (in the official repository) might solve your problem. It "mounts" FTP hosts as a local directory.
Then you could use rsync (or any other backup tool) to copy the files as though they were local files.

---

