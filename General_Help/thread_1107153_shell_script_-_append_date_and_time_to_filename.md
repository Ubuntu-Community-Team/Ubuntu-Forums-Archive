---
title: "shell script - append date and time to filename"
date: 2009-03-26
forum: General Help
---

### Post by talz13 on 2009-03-26
I have the following line in my backup script, just to drop a little one line log file date and time stamped when the script runs.  The date shows up alright on the filename, and the `date` command shows the correct date and time in the file.  running the `date +"%F--%k-%M-%S"` on the command line displays what I'm expecting, but it doesn't perform correctly in naming the file.

```
su jeff -c "echo Running backup script at `date` >> /home/jeff/backupLogs/backup-`date +"%F--%k-%M-%S"`.log"
```

```
jeff@parents-ubuntu:~$ echo `date +"%F--%k-%M-%S"`
2009-03-26--13-22-03
```

The filenames are showing up like this:```
backup-2009-02-08--12-50-52.log  backup-2009-02-18--  backup-2009-03-09--  backup-2009-03-24--
backup-2009-02-13--              backup-2009-02-27--  backup-2009-03-12--  backup-2009-03-25--
backup-2009-02-14--              backup-2009-02-28--  backup-2009-03-17--  backup-2009-03-26--
backup-2009-02-16--              backup-2009-03-08--  backup-2009-03-20--

```

The first file that actually has the correct filename was one that I was experimenting with while writing the script, and was run from the cli.  Any idea why it's not showing up when it's run from the script by a cron job?  The rest of the job completes normally...

If I take the shell script line and paste it on the command line, it works correctly and creates a file with a name of:```
backup-2009-03-26--13-25-17.log
```

---

### Post by kuja on 2009-03-26
It seems to be working for me. Hmm, what's wrong here?

---

### Post by musashixXX on 2009-03-26
Try changing this:

```
date +"%F--%k-%M-%S"
```

to this:

```
date +%F--%k-%M-%S
```

(in your script)

---

### Post by talz13 on 2009-04-02
> **musashixXX said:**
> Try changing this:

```
date +"%F--%k-%M-%S"
```

to this:

```
date +%F--%k-%M-%S
```

(in your script)

I just wanted to reply to say that removing the double quotes worked perfectly!  Thanks!

---

### Post by mike16889 on 2009-09-19
thanx, this thread helped alot, setting my server up to save verius programs on a local internet radio station and wanted it to save the file with time and date so as for easy identification

---

