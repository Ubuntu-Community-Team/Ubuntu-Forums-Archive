---
title: "w3m dump with cron not working"
date: 2009-02-17
forum: General Help
---

### Post by dinofizz on 2009-02-17
Ubuntu 8.04
kernel 2.6.24-23-generic

I'm trying to dump text from a website using w3m and cron.

This is what I'm using to test (excuse the use of the desktop as working folder!):

```
d@dtop:~/Desktop$ crontab -l
* * * * * /usr/bin/w3m -dump www.google.com | grep About >> /home/d/Desktop/google.txt
```

I can see that cron is running the command:

```
d@dtop:~/Desktop$ tail -n 20 /var/log/syslog
...
Feb 17 19:16:01 dtop /USR/SBIN/CRON[9302]: (d) CMD (/usr/bin/w3m -dump www.google.com | grep About >> /home/d/Desktop/google.txt)
...
```

But all that appears on the desktop is an empty file named 'google.txt'

Can anyone replicate this problem? What I am I doing wrong?

The w3m dump command works fine from the terminal.

**Interesting note:** If I make an executable script file containing:

```
#!/bin/sh
/usr/bin/w3m -dump www.google.com | grep About >> /home/d/Desktop/google.txt
```

then it WORKS if I run it from the terminal ( ./w3mdump.sh ) but it DOES NOT WORK if I 'double click' the script icon and then select the 'Run' button - creates empty google.txt file

---

### Post by yoyoned on 2009-02-17
try using the full path to grep

---

### Post by dinofizz on 2009-02-18
It is working now, thank you!

---

