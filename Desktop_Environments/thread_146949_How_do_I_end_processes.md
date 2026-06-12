---
title: "How do I end processes"
date: 2006-03-19
forum: Desktop Environments
---

### Post by kayas80 on 2006-03-19
I just checked my system monitor and noticed xscreensaver is sleeping (taking up valuable memory) even though I have screensaver disabled. I can end processes from the system monitor, though, upon reboot they start up again. How do you permantly disable processes?

---

### Post by taurus on 2006-03-19
You can use the kill command to kill a process, assuming you know the PID--number!
```

sudo kill -9 PID
-or-
sudo kill -9 1234

```

---

### Post by kayas80 on 2006-03-19
How do you find out the PID number? Also what is the -9 for?

---

### Post by christhemonkey on 2006-03-19
You can use the command
```
ps aux
```
to list all running proccesses.

---

### Post by Ramses de Norre on 2006-03-19
Isn't this the same as stopping the process in system monitor?
It will still start at every reboot, wont it?

---

### Post by kayas80 on 2006-03-19
[quote=taurus]You can use the kill command to kill a process, assuming you know the PID--number!
```

sudo kill -9 PID
-or-
sudo kill -9 1234

```[/quote]

I tried that did a reboot and the process started again. Any ideas How I can permantly end the process?

---

### Post by Ramses de Norre on 2006-03-19
You'll need to delete it somewhere, but I can't find where..
You'd search for the file/folder where is defined what to start when entering runlevel 2 (default runlevel).
It's not in /etc/rc2, and I don't find any other places where such scripts are stored to start at boottime.

---

### Post by kayas80 on 2006-03-19
[quote=Ramses de Norre]You'll need to delete it somewhere, but I can't find where..
You'd search for the file/folder where is defined what to start when entering runlevel 2 (default runlevel).
It's not in /etc/rc2, and I don't find any other places where such scripts are stored to start at boottime.[/quote]

Thanks for the help but i'll have to leave it. I wouldn't know where to start.

---

### Post by steve.horsley on 2006-03-19
What process is it? Try **sudo ps -ef** to see what command launched it.

---

### Post by kayas80 on 2006-03-19
[quote=steve.horsley]What process is it? Try **sudo ps -ef** to see what command launched it.[/quote]

I'm trying to end the screensaver. I entered that code and copied what it says when executing that command for the screensaver: -

UID        PID  PPID  C STIME TTY          TIME CMD
kayas80   7550     1  0 17:24 ?        00:00:00 xscreensaver -nosplash

---

### Post by az on 2006-03-19
Is it in System- Preferences - Session - startup programs?  (Dapper no longer uses xscreensaver, so I cannot check for myself...)

---

### Post by kayas80 on 2006-03-19
[quote=azz]Is it in System- Preferences - Session - startup programs? (Dapper no longer uses xscreensaver, so I cannot check for myself...)[/quote]

No it isn't.

---

