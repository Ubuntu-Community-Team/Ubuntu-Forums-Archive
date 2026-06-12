---
title: "What's the system doing on its own"
date: 2009-02-05
forum: General Help
---

### Post by sidewalkcynic on 2009-02-05
Several minutes into a session the operating system does something, but I haven't learned what it is yet... The system monitor shows activity in the background, and about 10% on the active side; and the hard drive is activated off and on for about five minutes.

What's going on?

---

### Post by drs305 on 2009-02-05
You could install "htop" if it is not already on your system. It shows running processes and you can use the F6 key to select the sort method. You might be able to see what process starts about the time you experience the disk writes.

To install and run:
```

sudo apt-get install htop  # to install
htop  # to run

```

Some straight command line entries that can show you the running processes, alhtough not as versatile as htop, are:
```

ps aux | less  # display all running processes (scroll to see more)
ps -u <username>  # Show your running processes  example:  ps -u *myusername*

```

---

### Post by sidewalkcynic on 2009-02-05
Thanks,

Now, if someone can remind me to do it when it happens:p

---

### Post by drs305 on 2009-02-05
I would imagine you would remember if you had set up any backup cron jobs, but you can check with the following:
```

crontab -l  # check your cron jobs
sudo crontab -l # check root's scheduled tasks

```

Sorry, can't help you remember... ;)

---

