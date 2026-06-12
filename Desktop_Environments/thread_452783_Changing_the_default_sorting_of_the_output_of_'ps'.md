---
title: "Changing the default sorting of the output of 'ps'"
date: 2007-05-23
forum: Desktop Environments
---

### Post by jetthe on 2007-05-23
I'm experiencing something strange on one of my Ubuntu installations. Something which started when upgrading to Feisty from Edgy. The output of 'ps axu' isn't sorted by starting time as it used to be. When runned on my other machine which is running Feisty (xubuntu) or on my Dapper server the same command sorts the output by starting time.

To illustrate: 

```

jetthe   10959  0.0  0.2   7308  3804 pts/3    Ss   May11   0:01 bash
jetthe   11297  0.0  1.7 106668 26604 ?        Sl   May20   1:11 gaim
jetthe   14865  0.3  1.3  96120 20624 ?        S    22:44   0:06 gnome-panel --sm-client-id 117f000001000117888036100000059570001 --s
jetthe   14909  0.0  0.5  28188  9208 ?        Sl   22:44   0:00 /usr/lib/evolution/2.10/evolution-exchange-storage --oaf-activate-ii
jetthe   15015 17.9  1.9 163344 30508 ?        SNl  22:52   4:35 /home/jetthe/bin/linuxdcpp
jetthe   15255  0.0  0.1   4628  2352 pts/1    S+   23:04   0:00 ssh 192.168.0.29
jetthe   15508  0.0  0.0   2560   996 pts/3    R+   23:18   0:00 ps aux
jetthe   16530  0.0  0.7  55016 12072 ?        S    May12   0:39 /usr/lib/notification-daemon/notification-daemon
118      17614  0.0  0.1   5484  2948 ?        Ss   May12   0:02 /usr/sbin/hald
root     17615  0.0  0.0   2876   876 ?        S    May12   0:00 hald-runner

``` 

seems rather strange, doesn't it? This occurs no matter which user I use for running the command.
I am grateful for any tips or ideas on how to solve this.

---

### Post by Metacarpal on 2007-05-23
As far as I understood, the default sorting order of the ps command, unless you tell it otherwise, is by PID.  Generally speaking, this will coincide with the starting time, since PIDs are assigned sequentially.  It's possible, however, for a new (or restarted) process to be assigned a previously-used PID which has become available due to the stopping of the previous process.

I think that's what you're seeing here.  Try:
> ps aux --sort=lstart

---

### Post by jetthe on 2007-05-31
> **Metacarpal said:**
> As far as I understood, the default sorting order of the ps command, unless you tell it otherwise, is by PID.  Generally speaking, this will coincide with the starting time, since PIDs are assigned sequentially.  It's possible, however, for a new (or restarted) process to be assigned a previously-used PID which has become available due to the stopping of the previous process.

I think that's what you're seeing here.  Try:

```
ps aux --sort=lstart
```



On my other machines the order is in fact by starting time and not by PID, which can easily be seen after a few wrappings of the PID numbers. 
The output from 
```
ps aux --sort=lstart
```

is still not ordered by starting time though...

```

jetthe   16464  0.0  0.2   7376  3848 pts/3    Ss   May30   0:00 bash
root     19235  0.0  0.1   9600  2844 ?        S    May28   0:39 /usr/sbin/smbd -D
jetthe   21184  0.0  0.2   7372  3840 pts/5    Ss+  12:21   0:00 bash
root     24454  0.0  0.0      0     0 ?        S    May30   0:01 [pdflush]
jetthe   25059  0.0  0.2   7372  3808 pts/4    Ss+  May30   0:00 bash
root     27626  0.0  0.1   7888  2396 ?        Ss   20:51   0:00 sshd: jetthe [priv]
jetthe   28474  0.0  0.0   2556  1024 pts/3    R+   22:03   0:00 ps aux --sort=lstart
jetthe   32387  0.8  2.9 214160 46096 ?        SNl  May29  35:23 /usr/local/bin/linuxdcpp

```


This seems very strange, I would like to see what the default order is on any other users feisty and/or edgy installations. So please, contribute! :]

---

