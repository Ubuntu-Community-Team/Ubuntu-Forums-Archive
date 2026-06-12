---
title: "hourly chime with crontab?"
date: 2005-10-11
forum: Desktop Environments
---

### Post by jamesford on 2005-10-11
just wondering what the crontab command for a hourly chime of some kind would be. for example playing a wav or mp3 (without opening a particular application like xmms) at the top of every hour

alternatively, how to add additional sound events executed at a particular time in system >prefs >sound

or other ways of achieving the same

---

### Post by ubuntumaneh on 2005-10-11
Check this, it is much better than the man page:

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

### Post by RikoW on 2005-10-12
just call on the command line:

```
> crontab -e
``` 

and it will open your crontab file with the default editor for editing.
Add the following line to the crontab file:

```
0 * * * *  play path-to-sound/sound.wav
```

save and quit the editor.

it will play the wav file *sound.wav* which is located in the directory  *path-to-sound*
at 0 minutes of every hour of every day of the week.

Check the link ubuntumaneh gave you above for the details of those * up there.

Have fun,
            Riko

---

