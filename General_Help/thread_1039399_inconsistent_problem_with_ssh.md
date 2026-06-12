---
title: "inconsistent problem with ssh"
date: 2009-01-14
forum: General Help
---

### Post by lsutiger on 2009-01-14
I will try to keep this as simple as possible. I have 2 computers, both running 8.04.
One computer is at work. The other at home.

I can ssh from home to work. But when I am at work, I can not ssh to home. BUT...and here is the kicker, when I am at home, I can ssh into the work computer and while I am in the shell, logged on to the work computer, I can ssh into my home computer!


I know this sounds a bit wacky, but I was trying to troubleshoot everything, so I just decided to try logging in to the home computer while remotely logged into work computer. 

I also have a 3rd 8.04 computer at the house, which I can remote into the home computer by local ip.

I am behind a firewall/router, and I do have the correct ports open. I also have ssh listening to an alternate point. ssh from work to home worked for a long time, then just stopped working about a week ago. Were there any updates for 8.04 that may have jacked up something to do with ssh?

Thanx for any replies!

---

### Post by lsutiger on 2009-01-14
Update - I tried tonight to do the doubleback remote and it did not work at first. I had to restart ssh, then it worked.

I checked to see if the ssh-agent was running before I did a restart, and it was.
 
Any ideas?

---

### Post by albinootje on 2009-01-14
> **lsutiger said:**
>  I can ssh from home to work. But when I am at work, I can not ssh to home. BUT...and here is the kicker, when I am at home, I can ssh into the work computer and while I am in the shell, logged on to the work computer, I can ssh into my home computer!

You can compare the output of 
```

set > set-output-1.txt

```

or perhaps more specific
```

set|grep -i ssh

```
between the two different sessions.

Are you using Network Manager on that work machine, or wicd, or do you have a manually configured /etc/network/interfaces ?

---

### Post by lsutiger on 2009-01-14
I have attached two files. One from the home computer, one while logged into the work computer.

---

### Post by albinootje on 2009-01-14
Your work to home has this (amongst others) as extra in the environment settings :

<             COMPREPLY=($( ssh -o 'Batchmode yes' $prev                    "ping -bnc 4 255.255.255.255" 2>/dev/null |                     awk -F ' ' '{print $4}' |                         sort -n | uniq | egrep '[0-9]+\.[0-9]+\.' 2>/dev/null ))

I don't know what that is about.

What happens actually when ssh doesn't work ? Do you get a time out in the end ?

---

### Post by lsutiger on 2009-01-14
Thanx for all your input ;)
I get a connection refused when it does not work

---

### Post by lsutiger on 2009-02-07
bump

---

