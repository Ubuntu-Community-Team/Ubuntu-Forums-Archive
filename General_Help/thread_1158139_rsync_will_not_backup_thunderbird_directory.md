---
title: "rsync will not backup thunderbird directory"
date: 2009-05-13
forum: General Help
---

### Post by startling on 2009-05-13
I'm trying to run rsync to make a daily backup of my /home/mark/.mozilla-thunderbird directory using this command:

```
rsync -arv /home/mark/.mozilla-thunderbird /media/truecrypt1/thunderbird
```

But rsync throws this error:
```
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
```

No files are copied to the target directory, which is a Truecrypt encrypted file on a removable USB hard disk mounted as a volume.

Ideally I'd like to make this a daily cron job, as a recent hard drive failure lost some of my email and I'd like to avoid that happening again!

---

### Post by alphaniner on 2009-05-13
Have you tried rsync'ing anything else to the Truecrypt file-volume?  I would suspect the problem is there, rather than with the T-bird directory.  The only other thing I would suggest is to make sure you have exited (not just closed) T-bird, but I doubt that's the cause of your problem in any case.

---

### Post by startling on 2009-05-13
Thanks for the speedy reply Alphaniner. Yes I tried rsyncing a dummy text file from my home folder and that worked correctly. 

I tried exiting Thunderbird but it made no difference (which I'm quietly relieved about because I would like the backup to be an automated process and not require me stopping and restarting Tbird).

---

### Post by alphaniner on 2009-05-13
All I can suggest is more experimentation...

Try without the 'a' flag.

Try rsyncing a directory rather than a single file to the Truecrypt file-volume.

Try rsyncing the T-bird directory to another location - preferably another HDD or the USB drive proper.  If that works, try rsyncing from there to the Truecrypt.

---

### Post by jowilkin on 2009-05-13
This may be a stupid question because you probably already checked, but is your directory really called ~/.mozilla-thunderbird?  Mine is ~/.thunderbird.

---

