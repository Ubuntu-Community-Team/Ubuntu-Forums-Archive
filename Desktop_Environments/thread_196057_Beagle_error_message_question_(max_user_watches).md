---
title: "Beagle error message question (max_user_watches)"
date: 2006-06-13
forum: Desktop Environments
---

### Post by dpm on 2006-06-13
Hi,

after starting the beagle daemon from the command line, I noticed that it was complaining about the following:

```
inotify_add_watch: No space left on device
Maximum watch limit hit. Try adjusting /proc/sys/fs/inotify/max_user_watches
```

After googling a bit, I found out that this is a common issue, as described at the Beagle wiki (Trobleshooting section):


> If you're getting this it's because beagle is hitting the kernel limit for the number of directories a single process can monitor. The default is 8192. 16384 is good, 32768 is probably more than enough. Notice that this will use more memory. 
To change the limit: 
 # echo 16384 > /proc/sys/fs/inotify/max_user_watches
To make the change permanent you should put that command in one of your boot scripts.


Ok, I understand how to solve it temporarily for a session, but I'm not sure how to do this part:

> To make the change permanent you should put that command in one of your boot scripts.

What's the best way to implement this with a startup script? Should I just create a script in init.d and get it to load at the appropriate runlevels?

Thanks in advance.

---

### Post by dpm on 2006-06-15
In the good ole tradition of answering oneself's posts:

1.-  Edit the sysctl.conf file:

```
sudo gedit /etc/sysctl.conf 
``` 
2.- Add this line to the end of the file:
```
fs.inotify.max_user_watches=16384
``` 
I might go and update the beagle wiki page if I can later on.

I hope this is useful to someone.

Cheers

---

### Post by m0bilitee on 2007-03-20
It's an old post, but I'm seeing this with Beagle running and then trying to mess with MonoDevelop on the same system.  Hopefully if someone else has the problem they view this.  I'm on 6.10 AMD64...

---

