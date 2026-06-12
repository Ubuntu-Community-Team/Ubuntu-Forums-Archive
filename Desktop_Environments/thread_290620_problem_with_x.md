---
title: "problem with x"
date: 2006-11-01
forum: Desktop Environments
---

### Post by kulashaker on 2006-11-01
Hi,

I installed Edgy a few days ago on my IBM T42 laptop. Everything has been working fine untill now. Suddenly xsession fails to begin, and I get an error message:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kula"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

```

So X starts up and I get the normal login screen. When I type in my login and hit enter, I get the above message. I've tried logging in with failsafe, but no dice.

Can anyone here help me out?

Thanks,
Kula

---

### Post by jimbren on 2006-11-01
take a look at the ownership of files in your /home directory.   would speculate that you'll see that something is no longer owned by you.

```
ls -a -l
```

If that's the case, then the easiest way to resolve it is to do 
```
sudo chown yourusername:yourgroupname *.*
```

If that's not the case, then it is likely a problem with your /tmp directory.  I believe you can take care of that by doing this:
```
sudo chmod 777 /tmp
```

Let me know how this goes.

Thanks,

jim

---

### Post by kulashaker on 2006-11-01
jimbren to the rescue!

Yay, I have now got my xsession/desktop back! *very happy* It seems to have been a problem with /tmp - wich I have chmod'ed to 777. I can't oversee the consequences of this action though... if any.

Thanks jimbren, nicely done!
Kula

---

