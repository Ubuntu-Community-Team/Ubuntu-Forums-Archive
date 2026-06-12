---
title: "Gnome keyring is using lots of memory"
date: 2015-02-25
forum: Desktop Environments
---

### Post by rleir on 2015-02-25
Gnome keyring is using lots of memory.  1.664g resident (see below). Maybe this is related: I have some automation running which starts many scripts on another server via ssh.  Also, I might have changed something in NetworkManager several months ago.

My question is: how best to troubleshoot this problem? Maybe run valgrind on gnome-keyring-daemon? The work-around is to log out and log in, but I would rather not do that. 

Ubuntu 14.04, updated in Jan 2015.

```
$ top -o RES

top - 09:58:28 up 18 days, 19:17,  8 users,  load average: 4.03, 4.19, 3.51
Tasks: 256 total,   5 running, 251 sleeping,   0 stopped,   0 zombie
%Cpu(s):100.0 us,  0.0 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16116496 total, 15680272 used,   436224 free,   372872 buffers
KiB Swap: 16456700 total,  2245644 used, 14211056 free. 10228548 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND  
 2283 fredd     20   0 3975336 1.664g   2528 S   0.0 10.8  19:22.55 gnome-keyring-d 
 9393 fredd     20   0 1396020 367076  56056 S   0.0  2.3   1:01.43 firefox  
 2680 fredd     20   0 1674516 336072  32388 S   0.0  2.1  21:59.35 nautilus  

$ ps -aef |grep gnome-keyri
fredd     2283     1  0 Feb06 ?        00:19:28 /usr/bin/gnome-keyring-daemon --daemonize --login
```

Thanks for help

---

### Post by rleir on 2015-02-27
Today we are up to 1.8g
```


$ top -o RES
[FONT=courier new]
top - 09:22:13 up 20 days, 18:41,  8 users,  load average: 1.27, 3.50, 3.96
Tasks: 264 total,   1 running, 214 sleeping,  49 stopped,   0 zombie
%Cpu(s): 84.6 us,  0.7 sy,  0.0 ni, 14.1 id,  0.6 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16116496 total, 15433612 used,   682884 free,   273356 buffers
KiB Swap: 16456700 total,  2366288 used, 14090412 free. 10074480 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND            
 2283 fredd     20   0 4237480 1.822g   2548 S   0.0 11.9  21:10.46 gnome-keyring-d 
 9393 fredd     20   0 1931424 765260  35480 S   6.5  4.7 129:59.66 firefox [/FONT]

```

---

### Post by oraslaci on 2015-06-02
Hi,

did you manage to sort out the issue?
I think this is somehow related to chromium browser and syncing its data.

Laszlo.

---

### Post by jcv2 on 2015-09-21
I'm using Chrome and having the very same issue.

I stopped using Chrome, but seems like this bug is still on. Any ideas to solve it?

---

### Post by VMC on 2015-09-21
I'm not having any of these issues. The first post shows the %CPU @ 100%?!
Also it shows Firefox. If your running Chrome, what's Firefox doing there?

EDIT: I just realized that this is a 7-month old topic. @ jcv2 best to start your own topic.

---

### Post by fabioxxxx on 2015-11-11
Same problem here.

Tested with chrome, making a login at **X** website (that had my credentials saved on the browser), gnome-keyring memory rose , logout and login again on the **same X** website keyring memory will rise again... by the end of the week gnome-keyring is using almost 200mb, since i have credentials saved for a lot of sites on chrome... For now i just reboot my workstation every week.

UBUNTU 14.04.03 
KERNEL 3.13.0-67-generic
google-chrome-stable 46.0.2490.80-1
gnome-keyring 3.10.1-1ubuntu4.2
Xfce 4.12

---

### Post by rolan1986 on 2016-03-16
hello! i have same problem.[IMG]http://s019.radikal.ru/i604/1603/a6/14f3960a58c3.png[/IMG]

---

