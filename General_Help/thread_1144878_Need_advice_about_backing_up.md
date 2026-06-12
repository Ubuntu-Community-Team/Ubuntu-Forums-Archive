---
title: "Need advice about backing up"
date: 2009-05-01
forum: General Help
---

### Post by ooobooontooo on 2009-05-01
Hi,

I want to upgrade from Hardy to Jaunty (been hearing a lot of good things about it). I know I can't directly upgrade from Hardy to Jaunty so I plan to back up all my data first and do a clean install of Jaunty. I just needed a couple pointers on some small issues that I've run into.

Right now I'm just basically doing:
```
tar -cpvzf hardy.backup.tgz /home/<user>
```
in the home directory.

Some errors I've seen are:
```
tar: Removing leading `/' from member names
tar: /home/<user>/hardy.backup.tgz: file changed as we read it

```

My questions are:
Do I even need to worry about the first one?
The file changing thing happened for a couple of files, but I would guess that's because I was browsing the web at the same time and that changed my mozilla profile. I'm not sure of what else would be changed as I do the tar, but just in case, is there a way to freeze the files so that tar doesn't error? Or should I just ignore the errors? When tar encounters a "file changed" error does it just not include it in the tarball or does it include the version it sees or does it corrupt the tarball/directory?

Thanks in advance.

---

### Post by ooobooontooo on 2009-05-04
bump

---

### Post by kpkeerthi on 2009-05-04
You are tarring hardy.backup.tgz to itself and hence the error. You should exclude the backup file to prevent it from being tarred to itself.

```

tar -cpvzf --exclude=hardy.backup.tgz hardy.backup.tgz /home/<user>

```

---

### Post by sahabcse on 2009-05-04
For backup and Restore the system follow belowurl

[http://sahabm.blogspot.com/2009/04/backup-and-restore-your-system-linux.html](http://sahabm.blogspot.com/2009/04/backup-and-restore-your-system-linux.html)

---

### Post by ooobooontooo on 2009-05-04
> You are tarring hardy.backup.tgz to itself and hence the error. You should exclude the backup file to prevent it from being tarred to itself.
Agreed. However, there are other files that will do this as well (change I mean). One being the firefox profile (because I was using it while I was tarring my home...watching the list of files that you're tarring grow gets boring after the first minute or so). My question is, can I just ignore these warnings? Or do I have to find a way to freeze the files before tarring them?

---

### Post by ooobooontooo on 2009-05-04
@ sahabcse
Thanks for the link. I've looked over it quickly, but I think I would still get the same problems that I mentioned in my first post. There is one tidbit in there that says I can ignore most of the warning that are given by tar; is that what you were referring to?

But excellent link on system restoration; I would use it if I was doing a full system restore.

EDIT: One key thing that I would like to know is whether tar will exclude a file that changes while it's tarring...if so, I would lose my firefox profile, something I would not want to do.

---

### Post by kpkeerthi on 2009-05-04
> **ooobooontooo said:**
> My question is, can I just ignore these warnings? 
Yes. But you must still exclude the backup file. 

> **ooobooontooo said:**
> Or do I have to find a way to freeze the files before tarring them?
There is no way to freeze the files. If you want to be absolutely safe, perform the backup from "Recovery Mode" or make sure you do not run any applications that could possibly alter your $HOME contents.

---

### Post by sahabcse on 2009-05-04
> **ooobooontooo said:**
> @ sahabcse
Thanks for the link. I've looked over it quickly, but I think I would still get the same problems that I mentioned in my first post. There is one tidbit in there that says I can ignore most of the warning that are given by tar; is that what you were referring to?

But excellent link on system restoration; I would use it if I was doing a full system restore.

EDIT: One key thing that I would like to know is whether tar will exclude a file that changes while it's tarring...if so, I would lose my firefox profile, something I would not want to do.

For firefox bookmark backup and restore click [here]("http://sahabm.blogspot.com/2009/02/mozilla-bookmark-backup-and-restore.html")

---

### Post by ooobooontooo on 2009-05-04
@ kpkeerthi
Thank you for your clear cut answer. Just to make sure one last time, the created tarball will have have some copy of the files that are changed while tar reads them? If you could answer this one last question, I would really appreciate it.

@ sahabcse
Thank you for the link, but I wish to copy my whole firefox profile (browsing history, settings and all that).

---

### Post by kpkeerthi on 2009-05-04
> **ooobooontooo said:**
> @ Just to make sure one last time, the created tarball will have have some copy of the files that are changed while tar reads them? 

The tar process is reading the file that is being updated by another process. It may lead to a corrupted file pushed into the backup.

---

### Post by ooobooontooo on 2009-05-04
Thank you. I think your answer is exactly the one I needed to hear.

---

