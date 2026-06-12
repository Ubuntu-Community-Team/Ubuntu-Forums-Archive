---
title: "Job scheduling not working"
date: 2008-12-10
forum: General Help
---

### Post by Velvet Ghost on 2008-12-10
I want to schedule a job at 2 A.M. (since downloads from 2 A.M. to 8 A.M. do not count towards the 2.5 GB monthly upload/download limit imposed by my ISP). I have issued the command:

$ crontab -e

and then typed:

00 02 * * * rtorrent sample.torrent

and saved and exited the vi editor with <ESC>:wq. However, the job fails to start at 2 A.M. Nothing happens.

1) I have the correct time set, and synchronized with ntp.
2) rtorrent works fine when invoked directly from the shell. The job scheduling doesn't work with transmission either, which also works fine normally.
3) ps aux | grep cron shows an entry for /usr/sbin/cron, i.e. the cron daemon is running.

What do you think is the problem?

Thanks in advance.

---

### Post by moberry on 2008-12-10
Paste in your /var/log/cron (or something similar)

---

### Post by Velvet Ghost on 2008-12-10
> **moberry said:**
> Paste in your /var/log/cron (or something similar)

There's no /var/log/cron or any other log file there with cron in its name. There's only /var/log/daemon.log. But cat /var/log/daemon.log | grep cron gives no output.

---

### Post by moberry on 2008-12-10
Do you have a newline at the end of the file?

---

### Post by Velvet Ghost on 2008-12-10
No, I don't. Don't tell me that it makes a difference?

EDIT: I just tried putting a newline there, but it still didn't work.

---

### Post by mike2357 on 2008-12-11
I suggest you change your command to:

00 02 * * * rtorrent sample.torrent > OUT 2>&1

This will cause output (including error messages) to be sent to an output file, called OUT, which you can review after 2:00 a.m. passes.  You can review the file for error messages.  The file will be created in the home directory of the user whose cron file has the command.

---

### Post by moberry on 2008-12-11
> **Velvet Ghost said:**
> No, I don't. Don't tell me that it makes a difference?

EDIT: I just tried putting a newline there, but it still didn't work.


Yes, it does make a difference.

---

### Post by Velvet Ghost on 2008-12-12
> **mike2357 said:**
> I suggest you change your command to:

00 02 * * * rtorrent sample.torrent > OUT 2>&1

This will cause output (including error messages) to be sent to an output file, called OUT, which you can review after 2:00 a.m. passes.  You can review the file for error messages.  The file will be created in the home directory of the user whose cron file has the command.

I tried it. Here's what the OUT file contains:

rtorrent: PollEPoll::insert_read(...) epoll_ctl call failed

Any ideas?

---

### Post by moberry on 2008-12-12
that says that rtorrent is running, but crashing. It might have something to do with running under a cron job. You could try faking it with a shell script maybe.

---

### Post by Velvet Ghost on 2008-12-13
> **moberry said:**
> that says that rtorrent is running, but crashing. It might have something to do with running under a cron job. You could try faking it with a shell script maybe.

I tried it. It didn't work. Then I redirected output to the OUT file. This time it contained:

Error opening terminal: unknown.

---

### Post by ju2wheels on 2008-12-13
You should really be using absolute paths for both rtorrent and the torrent file...

---

### Post by Velvet Ghost on 2008-12-13
Anyway, I solved the problem - now I start up rtorrent and keep it running, and just schedule my network daemon to start up at 2 A.M. Its working now. Thanks, everybody.

---

