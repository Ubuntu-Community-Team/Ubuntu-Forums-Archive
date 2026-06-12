---
title: "Gnome apps start very slow after updates"
date: 2006-11-26
forum: Desktop Environments
---

### Post by pjbgravely on 2006-11-26
There was a bunch of updates for edgy a little while back. I installed them and shut down. Ever since I have used this laptop all Gnome apps are starting super slow. It takes between 30 sec and a Minute for them to come up, when before it was a few seconds. Non Gnome apps come up just fine, unless they are started by nautilus, then they are just as slow. 

  It is almost like there is a delay timer. during the waiting there is little CPU or disk drive activity. After running for a while the problems gets better.
I was wondering if this was happening to others or am I the only one.

Paul

---

### Post by ryurhrt on 2006-11-26
maybe is the network problem.

try:

sudo gedit /etc/hosts

change

127.0.0.1 localhost

to

127.0.0.1 <hostname> localhost

<hostname> refer to ur own hostname.

---

### Post by pjbgravely on 2006-11-26
Thanks that was the problem.

The last time I had a bad hostname Gnome wouldn't even start. That was a while ago and on a much older version. On my sever I misspelled the host name hosts and sudo broke. I guess edgy deals better with host name problems.

---

### Post by asnd16 on 2007-01-29
wow, that was the only thing I did that day to change I thought I allready deleted all the host IP information for that connection, and Obviously I did not! THANX

---

### Post by nimphelos on 2007-03-21
That was so easy and took too much time. Thanks for your answer.

---

