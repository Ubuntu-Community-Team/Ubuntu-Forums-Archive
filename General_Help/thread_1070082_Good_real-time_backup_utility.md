---
title: "Good real-time backup utility?"
date: 2009-02-14
forum: General Help
---

### Post by solwic on 2009-02-14
I recently bought an external 640GB USB hard drive.  It boots with my PC and shuts down with it, so when the PC is on, the HDD is on.  

I'm looking for a good backup utility that will backup my home folder and do regular backups of individual files as they are modified.  

I've looked at rsync, but unless I'm misunderstanding it, it's only for remove backups, isn't it?  

Any help would be great.  Thanks.

---

### Post by cdtech on 2009-02-14
Have a look here:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by solwic on 2009-02-14
> **cdtech said:**
> Have a look here:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

I'll check it out.  Are there any alternatives, or is rsync the best option?

Thanks for the link.  :)

---

### Post by HermanAB on 2009-02-14
Rsync can be use as a 'better kind of cp' on any machine. Read the man page. Most backup systems use rsync somewhere deep down underneath.

Cheers,

Herman

---

### Post by solwic on 2009-02-14
So let me make sure I have this straight.  If I have a directory called /home/user and I want to back it up to /media/External then the command I would use is:

```
rsync -a /home/user/ /media/External
```

Right?  And that command would only add files that haven't been backed up, or that have changed since the initial backup?  If I add it to crontab I can have it run every couple of hours, right?  

Or am I missing something?  Also, does rsync come preinstalled with Ubuntu?

Sorry, I'm a backup newb.  I know I should be doing this stuff, but haven't had adequate space until recently.  Now I want to learn all I can. :)

Thanks for the help.  :)

---

