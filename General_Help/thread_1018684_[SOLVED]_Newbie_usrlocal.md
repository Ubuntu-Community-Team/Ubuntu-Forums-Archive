---
title: "[SOLVED] Newbie: /usr/local"
date: 2008-12-22
forum: General Help
---

### Post by sylver1109 on 2008-12-22
For some reason I try to put /usr/local on a new partition AFTER ubuntu installation.

I mount my new partion to /mnt/newlocal. I copy the content of  /usr/local with nautilus in /mnt/newlocal. After 2.1gig of copy I decide to cancel because I forgot to show hidden files.

So I decide to delete the content of /mnt/newlocal befor try to copie again. I have run 'sudo rm -R /mnt/newloca/*'. I think somiting goes wrong because /mnt/newlocal is empty and /usr/local content of sub-forlder is empty.

Now I have two question. 
1 - How should I delete the file to keep /usr/local intact?
2 - Why after a reboot, Ubuntu run very well without missing program? What I have just deleted?

---

### Post by taurus on 2008-12-22
How did you copy /usr/local to /mnt/newlocal?

---

### Post by sylver1109 on 2008-12-22
I opened a terminal, 'sudo nautilus'. Open /usr/local. selecet all file (with the mouse). ctrl+C. Open /mtn/newlocal. ctrl+V

---

### Post by taurus on 2008-12-22
What's the output of this command from a terminal?

```
ls -la /usr/local
```

---

### Post by sylver1109 on 2008-12-22
I'm at work. I will check this evening. 
But if I rember well, all folders are empty except the 2 or 3 last. This is the 2 or 3 that have not being copied because I canceled them.

thx for the help.

---

### Post by sylver1109 on 2008-12-22
as you ask:

```
ls -al /usr/local
total 40
drwxr-xr-x 10 root root 4096 2008-10-29 18:53 .
drwxr-xr-x 13 root root 4096 2008-12-14 22:57 ..
drwxr-xr-x  2 root root 4096 2008-10-29 18:53 bin
drwxr-xr-x  2 root root 4096 2008-10-29 18:53 etc
drwxr-xr-x  2 root root 4096 2008-10-29 18:53 games
drwxr-xr-x  2 root root 4096 2008-10-29 18:53 include
drwxr-xr-x  3 root root 4096 2008-10-29 18:53 lib
lrwxrwxrwx  1 root root    9 2008-11-04 19:25 man -> share/man
drwxr-xr-x  2 root root 4096 2008-10-29 18:53 sbin
drwxr-xr-x 12 root root 4096 2008-12-17 17:18 share
drwxr-xr-x  2 root root 4096 2008-10-29 18:53 src
```

---

### Post by taurus on 2008-12-22
What about

```
du -h /usr/local
```
Here is the last line of the output on my machine.

```
148K	/usr/local
```
As you see, /usr/local is more or less empty unless you have installed something to /usr/local/bin.

---

### Post by sylver1109 on 2008-12-22
Mine is 136K. The only weird thing is the first time I copied all files it take like 10 minutes...

My ubuntu install was new so I decide to re-install, When I will be at the same point of installed programs, I will post the size of my /usr/local. Mabey it will be usefull for others.

Thx for the help.

---

### Post by sylver1109 on 2008-12-22
After re-instalation, I confirm that /usr/local is empty. I realy don't know what the first time I was copying then. Sorry for posting this question.

---

### Post by albinootje on 2008-12-22
> **sylver1109 said:**
> After re-instalation, I confirm that /usr/local is empty. I realy don't know what the first time I was copying then. Sorry for posting this question.

By default after a fresh installation /usr/local/ has only a structure of sub directories, but no files.
Only if you compile from source with the ./configure;make;sudo make install stanza, then usually files end up in /usr/local/

Can you mark this thread as SOLVED ?

---

