---
title: "Strange behavior of gnome-schedule"
date: 2009-11-22
forum: Desktop Environments
---

### Post by habib_seif on 2009-11-22
Hi all,

I would like to save my internet traffic every minute, so I created a task in gnome-schedule that its command is:
```

iptables-save -c > mydata

```
After applying the task, mydata file is created but its size is zero and no data is in the file :-(
By the way, gnome-schedule works good with all of the other commands such as:
```

ls -l > mydata

```

I added the line:
```
* *     * * *   root    iptables-save -c > mydata
```
into the /etc/crontab and it works perfectly but why the gnome-schedule can't do the job for this command?

P.S: I use "gksudo gnome-schedule" to run the gnome-schedule program.

Thnaks,
Habib

---

### Post by habib_seif on 2009-11-23
My problem was solved...

The gnome-schedule program does not include any path for executing commands, so changing the command to
```

/sbin/iptables-save -c > mydata

```
solved the problem

---

