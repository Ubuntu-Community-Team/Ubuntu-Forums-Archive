---
title: "how to import an old /home from another partition"
date: 2009-06-25
forum: General Help
---

### Post by amityak on 2009-06-25
Hello there

So after messing around a bit too much with my old ubuntu ive re-installed it, this time with KDE which i find much nicer then Gnome, but that is another discussion.

I am messing around with it for a while now, also googling didnt raise any results i was satisfied with. so here is my question:

how can I easily use the partition ( /dev/sda5 in this case, which was my /home directory of an ubuntu installation, a genome one. ) as the home directory of my new default user?

I have already tried just to mount it, or to mount it into a new user account it all caused millions of problems, so now i am able to access all the content but just as root and not as convinient as just accessing /home/music for example.

one more thing, copying the files is not an option because i want to use this partition and also for future updates/upgrade/re-installing-due-to-machine-crash-after-messing-around-too-much 


thank ya' all

Amit:P

---

### Post by statistic on 2009-06-25
When you mount the partition, what user does it say has ownership of the files? Is it root? or Another user? or nobody?

---

### Post by amityak on 2009-06-25
i think root

```
root@amit-desktop:/home/jts# ls -l
total 104
drwxr-xr-x   2 jts  root  4096 2009-06-24 20:41 Desktop
drwxr-xr-x   4 jts  root  4096 2009-06-23 23:04 Documents
drwxr-xr-x  17 root root  4096 2009-06-23 23:58 Downloads
drwxr-xr-x   2 root root 49152 2009-02-19 23:39 lost+found
drwxr-xr-x 129 jts  root  8192 2009-06-23 23:05 Music
drwxr-xr-x   6 jts  root  4096 2009-06-23 23:09 Pictures
drwxr-xr-x   2 jts  root  4096 2009-06-23 17:49 Public
-rw-r--r--   1 jts  root  1855 2009-06-23 17:50 screen-configurations.xml
drwxr-xr-x   7 root root  4096 2009-06-23 17:54 Studium
drwxr-xr-x   4 root root  4096 2009-06-23 17:45 stuff
drwxr-xr-x   2 jts  root  4096 2009-06-23 17:49 Templates
drwxr-xr-x   2 root root  4096 2009-06-23 19:24 todelete
drwxr-xr-x   4 jts  root  4096 2009-06-24 21:07 Videos
drwxr-xr-x  16 jts  root  4096 2009-06-24 20:44 workspace

```

jts is btw the mounted directory i want to import. 'amit' is the main user i would like to stay with, ive mounted it as 'jts' because i tried to open a new account
using this directory what caused some other problems

---

### Post by statistic on 2009-06-25
You may want to try using chown if you haven't given that a go yet. 

```
sudo chown amit file
```


If you're feeling brave cd into the directory and try 
```
sudo chown -R amit ./*
```

That will recursively change the permissions on every file in the directory to amit ownership. You proceed with that at your own risk.

If anyone knows of a safe solution please do tell.

---

### Post by amityak on 2009-06-25
well i just said

chown -R amit /home/jts

worked like charm!!
there is no safety issue because you dont actually change the files as far as i understand it, just their signatue
now i have to think how to combine my files into /home/amit so it would feel and look natively so i can let my ubuntu crash again without killing all my files (:


bless you (:

---

