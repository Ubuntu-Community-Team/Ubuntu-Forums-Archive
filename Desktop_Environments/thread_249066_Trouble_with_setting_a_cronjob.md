---
title: "Trouble with setting a cronjob"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Cable on 2006-09-02
I'm trying to set cron to start gwget.  I'm just testing right now to see if I can get it to do what I want, and I can't.  Here is what my line looks like...
```

11 1 * * * /usr/bin/gwget

``` That *should* start gwget at 1:11 AM every morning, correct?  It's not doing anything...

---

### Post by ayoli on 2006-09-02
edit, i ve said bullshit. according to the man 5 crontab that should be ok 11th minute after 1 am everyday.
another possibility is the path for gwget ok ? btw for bins that are in a path stored in $PATH you don't have to put all path.

regards.

---

### Post by ayoli on 2006-09-02
just tested a similar line
```
18 10 * * * /usr/bin/gnome-terminal
```
with or without full path, doesnt work :( 
holy crap ! i used to manage working cronjobs long time ago, i have to remind how..
EDIT: syslog show that cron run the command, but gnome term won't show

---

### Post by ayoli on 2006-09-02
ok, new test: 
```
*/2 * * * *     echo `date` " --> blah !" >> $HOME/crontest
```
works every 2 minutes:
```
[10:39:12@ayoli.zone]:~ >$ cat crontest
samedi 2 septembre 2006, 10:34:01 (UTC+0200)  --> blah !
samedi 2 septembre 2006, 10:36:01 (UTC+0200)  --> blah !
samedi 2 septembre 2006, 10:38:01 (UTC+0200)  --> blah !

```
but this line:
```
*/2 * * * *     /usr/bin/gnome-terminal
```
doesnt work. does it mean that cron is not able to run grapical apps ?

EDIT: syslog show that cron run the command, but gnome term won't show
```
Sep  2 14:50:01 localhost /USR/SBIN/CRON[19820]: (ayoli) CMD (/usr/bin/gnome-terminal^I)
Sep  2 14:52:01 localhost /USR/SBIN/CRON[19897]: (ayoli) CMD (/usr/bin/gnome-terminal^I)
Sep  2 14:54:01 localhost /USR/SBIN/CRON[19973]: (ayoli) CMD (/usr/bin/gnome-terminal^I)
```

---

### Post by Cable on 2006-09-03
Bump...anyone know what I'm doing wrong?

---

### Post by ayoli on 2006-09-03
nothing wrong. look in your syslog you will see cron run your command but if command is a gui app it seems it's not capable to run it.
see posts above i've edited.
however if someone now a way to launch an gui app with a cronjob ...let us know :)

---

### Post by kh4nh on 2006-09-03
you need to set the enviroment variable, try this:

18 10 * * * DISPLAY=:0 /usr/bin/gnome-terminal

---

### Post by ayoli on 2006-09-03
hell YEAH ! that works ! thx kh4nh ;)
i thought about setting display but using option like --display which didn't work, didnt think about environement var, thx again.

---

