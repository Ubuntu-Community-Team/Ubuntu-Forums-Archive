---
title: "Startup and Sound Problems (please help)"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Guild220 on 2006-06-28
I've been using Ubuntu for a while now, I got everything up and running perfectly, except the sound was a little buggy and wouldn't work sometimes when I was running more than one program at once.  So, I decided to download the Realtek sound drivers for linux to see if that would clear some of the minor problems up.  So I downloaded the .tar.gz, and did the old ./install, and it removed my original sound drivers and attempted to reinstall the new one.  Well, I got an error, but I assumed a restart would fix things.

Oops.

Now I can only log in to a terminal only session; every other time I try to log in I get this error message when I view the error log:

```
/etc/gdm/xsession: Beginning session setup
x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```

So basically, the only way to remedy this (I assume) would be throught terminal, and terminal only.

Anybody have any ideas?
Thank you very much.

(Oh, and I am having to use Windows right now to post this)

---

### Post by Guild220 on 2006-06-28
Or maybe I could reinstall ALSA?  But how would I do that through terminal only?

---

### Post by si_harp on 2007-06-11
Hi all,

I'm having exactly the same problem on my FS Amilo 1437G laptop!

Anyone managed to sort this?

Thanks. si

---

### Post by si_harp on 2007-06-15
bump

---

### Post by si_harp on 2007-06-15
FIXED!  :D

Found this thread [http://ubuntuforums.org/showthread.php?t=461894](http://ubuntuforums.org/showthread.php?t=461894) 

With thanks to engla who suggested trying...
[B]
*apt-get install --reinstall libasound2*[/B]

Fixed the problem, didn't even need to reboot to log on properley!  

Hope this helps someone. Si

---

