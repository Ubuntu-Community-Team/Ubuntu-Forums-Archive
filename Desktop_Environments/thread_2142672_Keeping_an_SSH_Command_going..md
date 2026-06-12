---
title: "Keeping an SSH Command going."
date: 2013-05-06
forum: Desktop Environments
---

### Post by Geffers on 2013-05-06
I have a Raspberry Pi set up for background tasks, one of which is to upload files to dropbox via command line scripts.

I can easily start this by ssh but would like this to continue when I close the ssh connection.

Any suggestions how this can be done.

Geffers

---

### Post by prodigy_ on 2013-05-06
If you just want background tasks append **&** (after a whitespace) to the command line. If you want tasks to start automatically (at reboot or at predefined time), see: ```
man 5 crontab
```

---

### Post by matt_symes on 2013-05-06
Hi

You could also look at 

```
screen
```

Detach and reattach to the screen session.

Kind regards

---

### Post by Cheesehead on 2013-05-06
Look into the 'screen' command. I use screen a bit like this on a remote system:

```
local:~$ ssh remote
remote:~$ps -e | grep screen
 5366 tty3    00:00:00 screen
remote:~$ screen -r 5366 [TAB]
remote:~$ run_new_tasks_within_screen
remote:~$    [ctrl + A] [ctrl + D] (exit screen)
[detached from 5366.tty3.remote]
remote:~$ exit
local:~$
```

Another option is to use Upstart jobs, which don't need ssh to stay live. 

```
local:~$ ssh remote
remote:~$sudo initctl emit do-the-backup-signal
[sudo] password for you:
remote:~$ exit
local:~$
```

Another option is to simply add it to your other weekly cronjobs.

---

### Post by Geffers on 2013-05-06
Solved, used tmux.

Geffers

---

### Post by Geffers on 2013-05-06
> **Cheesehead said:**
> Look into the 'screen' command. I use screen a bit like this on a remote system:

[CODE]local:~$ ssh remote
remote:~$ps -e | grep screen


A more in depth search suggested tmux is better than screen, thanks for pointer though, it pushed me in the right direction.

Geffers

---

