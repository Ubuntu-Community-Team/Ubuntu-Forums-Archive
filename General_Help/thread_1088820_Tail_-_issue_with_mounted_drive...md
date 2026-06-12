---
title: "Tail - issue with mounted drive.."
date: 2009-03-06
forum: General Help
---

### Post by Tom_T on 2009-03-06
I've mounted a network share using:

```
sudo mount -t cifs //192.168.10.10/c$ -o username=USERNAME,password=PASSWORD /mnt/server
```

After doing this I can access /mnt/server and see the files fine.

I've tried to tail a log (.txt) file on the share. It seems to work, but the tail never shows the updates as the file changes.

```
tail -f /mnt/server/apps/logs/logfile.txt
```


I've also tried this using System Log and KSystemLog, but they never update to show the new entries in the log file..

What have I done wrong or missed ??

The share is on a Windows 2003 server (NTFS)

Thanks:)

---

### Post by Xiong Chiamiov on 2009-03-07
Due to the way Windows shares are dealt with in Linux, it's highly likely that tail will never recognize file updates on your server.

---

