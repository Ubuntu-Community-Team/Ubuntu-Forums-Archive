---
title: "Cron job to shutdown Ubuntu"
date: 2008-09-20
forum: Desktop Environments
---

### Post by jcoyle on 2008-09-20
Hi,

I realise this question has been asked / answered a thousand times, but i am having problems.

I want to set up a cron job to shutdown my ubuntu box at say 11:45 each night, so i do the following:

1. Log on as root
2. ```
 crontab -e 
```
** Here a get a NANO window where i add this: 
3. ```
 45 23 * * * /sbin/shutdown -h 
```
4. i then press CTRL-O to WriteOut the file, and leave the default name as it is
5. Terminal displays ```
crontab: installing new crontab
```

When 11:45 comes, it does not shutdown or anything.

I am doing something wrong?

Any insights / help appreciated. 

Thanks

Joe.

---

### Post by Monotoko on 2008-09-20
there is already a way to do this:

sudo shutdown -h 23:45
that would make it shutdown at 23:45 :)

---

### Post by jcoyle on 2008-09-20
thanks for quick response - will 

sudo shutdown -h 23:45 

do it every day though?

thanks

---

### Post by Monotoko on 2008-09-20
If you put it in a script and make it start at bootup, yes :)

sorry for the late reply, i went offline

---

### Post by jcoyle on 2008-09-20
hi,

how would i go about doing that? where would i need to save the file? 

thanks.
J.

---

### Post by marcthenarc on 2008-09-20
I think it would be easier to use 'shutdown -h now' at the required time.

If you set a time at the end of the shutdown command, chances are, if your system is quite busy, that the cron job will start just *after* 23:45 and then issue a shutdown command that will trigger a shutdown 24 hours later (or rather 23 hours 59 minutes and a few seconds later).

```

# Shutdown system at 23:45 every day
45 23 * * * /sbin/shutdown -h now

```

You are then sure that the shutdown command will execute at 23:45 (give or take a few seconds).

---

### Post by mister_p_1998 on 2008-09-21
Well my machine shuts down evey day & I do this:
sudo gedit /etc/crontab

put your command in here (it runs crontab as root)

---

### Post by directcharitycontribution on 2008-09-25
Code: 0 3 * * * /sbin/shutdown now

---

### Post by aquinn on 2009-07-10
@mister_p_1998: Excellent tip, thank you. 

Here's what I did:

[LIST=1]
[*]Open /etc/crontab: ```
sudo gedit /etc/crontab
```
[*]Add following to end of file: 
```

# At 23.30 every evening shutdown with 1 minute's notice
30 23    * * *    root    shutdown -h +1

```
[*]Save and close file
[/LIST]
If you're unsure of your crontabbing skills, you can add a simple test to /etc/crontab:
```

# "touch" a test file every minute
* *    * * *    root    touch /tmp/root-crontab-test

```This should create a new file called "root-crontab-test" in the /tmp directory on the first invocation, and then update the "last modified" date every minute. You can monitor this by running: 
```
ls -l /tmp/root-crontab-test
```You should see something like:
```
-rw-r--r--  1 root   root         0 2009-07-10 21:10 /tmp/root-crontab-test
```

---

