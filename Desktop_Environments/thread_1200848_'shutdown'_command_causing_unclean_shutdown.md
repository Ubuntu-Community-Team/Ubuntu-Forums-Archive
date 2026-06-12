---
title: "'shutdown' command causing unclean shutdown"
date: 2009-06-30
forum: Desktop Environments
---

### Post by silentwol on 2009-06-30
Hi, hope you can help.

I'm running a backup script, which when finished immediately issues the command:
```
sudo shutdown -h now
```

I believe this is causing the error I get the next time the computer starts, something like "unclean shutdown detected, fsck forced".

I've cycled through some 'normal' restarts in KDE and I don't get the error.  Could it be the above shutdown command?  If so, is there a 'safe' way of shutting down the computer?

Thanks! :)

---

### Post by mcduck on 2009-06-30
That command should do a clean shutdown..

Are you running any of the commands in your script in background? Perhaps they haven't finished yet when the script executes the shutdown command..

---

### Post by silentwol on 2009-07-01
I added a two minute delay to the shutdown command and the error didn't occur.  Fingers crossed it wont happen again :)

---

### Post by silentwol on 2009-07-28
Sorry to drag this thread up again, but I still haven't found a solution.

I've just been playing with it and I've found that when I try to unmount the filesystem I get this error:
```

$ sudo umount /dev/md0
umount: /backup: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

If it's busy (and can't be properly unmounted on shutdown) could this be a the cause of my problems?

Edit: Beer and linux don't mix! I was in /backup when trying to run umount. DOH.

---

