---
title: "shutdown utility with countdown timer and notification"
date: 2008-07-01
forum: Desktop Environments
---

### Post by badkuk on 2008-07-01
Hi All,

First post B)

i am looking for a utility the behaves similarly with this command on windows xp:

 
shutdown.exe -s -f -t 600 -c "shutdown in 10 min. open a command prompt and run shutdown -a to cancel"


Basically the command , when run via Scheduled tasks, will display a shutdown notification message for 10 minutes, warning the user about imminent shutdown, and will abort the shutdown once a shutdown -a command is issued; otherwise it's lights out.

i've tried gshutdown, but my main complaint is that somebody will have to manually run it first, not to mention manually set the shutdown schedule, for it to work. afaik i can't pass any parameters to it, so i can't schedule it via cron.


Any suggestions are welcome. tia

---

### Post by ramaswamyps on 2008-07-01
you must be able to use orage for this purpose.i think.
set alarm command to shutdown now

---

### Post by LinuX-M@n1@k on 2008-07-01
Try gshutdown ?
```
sudo aptitude install gshutdown
```

EDIT: sorry, just read that you already tried it xD

---

### Post by Vivaldi Gloria on 2008-07-01
There is a shutdown which can do all the things you want in command line. For example

```
sudo shutdown -h +15
```

will shutdown the system in 15 mins. You can cancel it with sudo shutdown -c. See

```
man shutdown
```

for more info.

Now you can save a text file which says the system will shutdown in 15 mins. Write a script:

```
#!/bin/bash
aplay sound.wav
pop up that text file you saved with an editor of your choice
shutdown -h +15
```

Or you pop up a message with zenity, etc. You get the idea.

---

### Post by olskar on 2008-07-13
I have modified the timerapplet that is in the repos to a turnoff-timer (gotta love linux) and I am very pleased :)

---

### Post by Big Wig !!! on 2008-07-26
Try SuperAwesomeTimer2000 great program.:KS

---

