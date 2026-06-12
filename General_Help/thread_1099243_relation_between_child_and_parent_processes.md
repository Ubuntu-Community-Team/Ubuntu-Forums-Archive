---
title: "relation between child and parent processes"
date: 2009-03-18
forum: General Help
---

### Post by divya thakur on 2009-03-18
i have a problem understanding the relationship between child process and parent process.A child process has a PPID and PID different from the PID of its parent process.how this is happens.Please explain

---

### Post by pbpersson on 2009-03-18
Well....I'm sorry.....I know what a PID is, but what is a PPID and where are you seeing all this?

---

### Post by bab1 on 2009-03-18
@pbpersson,

PPID + Parent Process IDentifier

@divya thakur,

"*the relationship between child process and parent process...*

The parent process is the original process invoked.  This can be from the CLI or by script or upon boot up.  In any event, typically, the process (daemon/server) runs in the background until a request for service is detected from a client host.  At this point the process spawns a child process to handle the request and returns to listening for additional requests for service.

Let's look at how this can be monitored.  Below is what the smbd service (Samba server) looks like with no requests (just listening):```
bruce@malibu:~>ps -ef |grep smbd
root      4431     1  0 21:10 ?        00:00:00 /usr/sbin/smbd -D
root      4480  4431  0 21:10 ?        00:00:00 /usr/sbin/smbd -D
bruce     5237  5219  0 22:53 pts/0    00:00:00 grep --color=auto smbd

```

The 2 smbd -D processes are normal running.  The PID's are 4431 and 4480.

Now let's look at the same processes as I browse a Samba share:```
bruce@malibu:~>ps -ef |grep smbd
root      4431     1  0 21:10 ?        00:00:00 /usr/sbin/smbd -D
root      4480  4431  0 21:10 ?        00:00:00 /usr/sbin/smbd -D
smbguest  5251  4431  0 22:55 ?        00:00:00 /usr/sbin/smbd -D
smbguest  5252  4431  0 22:55 ?        00:00:00 /usr/sbin/smbd -D
smbguest  5261  4431  0 22:55 ?        00:00:00 /usr/sbin/smbd -D
bruce     5286  5219  0 22:55 pts/0    00:00:00 grep --color=auto smbd

```
The original parent PID's are still there, but the request has been handled by the child PID's 5251/5252 and 5261. Note that the PPID (2nd column) is 4431 for all.

---

