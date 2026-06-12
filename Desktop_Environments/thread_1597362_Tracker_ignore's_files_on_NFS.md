---
title: "Tracker ignore's files on NFS"
date: 2010-10-15
forum: Desktop Environments
---

### Post by denarced on 2010-10-15
I had the same setup on Karmic, one directory under homedirectory, to which the nfs is mounted. Worked fine in Karmic. But now in Maverick, it ignores all the files on the NFS-folder. It finds directories fine and lists them in log-files. I've set the logging to debug(3) where-ever possible.

For example, from /home/denarced/.local/share/tracker/tracker-miner-fs.log:
```

15 Oct 2010, 14:00:08: Tracker:   Found 2584 directories, ignored 56 directories
15 Oct 2010, 14:00:08: Tracker:   Found 39738 files, ignored 588 files
15 Oct 2010, 14:00:08: Tracker: Finished crawling files after 11.30 seconds
15 Oct 2010, 14:00:08: Tracker: Checking if any file was removed...
15 Oct 2010, 14:00:08: Tracker: Processingâ<80>¦

```

File system is still 1% in the my top manel while Applications and emails are 100%.

What could cause this ?

---

### Post by denarced on 2010-10-24
Anyone, anything.
Things to check, logs to insert here ?

---

### Post by denarced on 2010-10-24
I have now checked that:
[LIST]
[*]tracker-miner-fs seems to at least go through the files on the mounted nfs-share. Or at least it accesses files all the time.
[*]tracker-extract is never on the process list.
[*]tracker-extract works when executed manually on a single file.
[/LIST]

Interesting thing which could be just a coincidence. I checked /var/log/syslog and found constant error messages:
```

Oct 24 22:17:56 denarced-desktop rpc.statd[849]: No canonical hostname found for 192.168.11.6
Oct 24 22:17:56 denarced-desktop rpc.statd[849]: STAT_FAIL to denarced-desktop for SM_MON of 192.168.11.6
Oct 24 22:18:01 denarced-desktop rpc.statd[849]: No canonical hostname found for 192.168.11.6
Oct 24 22:18:01 denarced-desktop rpc.statd[849]: STAT_FAIL to denarced-desktop for SM_MON of 192.168.11.6
Oct 24 22:18:01 denarced-desktop kernel: [ 3310.994163] lockd: cannot monitor 192.168.11.6

```

I checked and these error messages did not appear when I was running tracker on karmic. The nfs-server is still the same, only the client machine has changed. The IP-address belongs to the nfs-server.

---

### Post by denarced on 2010-10-24
This problem has been solved by adding the hostname of the nfs-server to /etc/hosts. I don't know why that solved the problem and I'd like to know if someone knows what's going on.

---

