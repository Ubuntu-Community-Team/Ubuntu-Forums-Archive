---
title: "I need an application that will shut down the desktop..."
date: 2009-03-09
forum: General Help
---

### Post by 3pinner on 2009-03-09
at a predetermined time, and not allow logon until another pre determined time.
So family won't be on the computer all night long! 

Any suggestions?
Is that feature in the server version of Ubuntu, if it is I'll wipe the desktop, and install server instead.

Thanks

---

### Post by heindsight on 2009-03-09
That depends on how they're logging in. If they log in remotely through ssh, you can easily schedule a cron job kill the ssh server at a given time and then restart it again later.

If they have physical access and log in directly, the only thing I can think of is to do:
```
touch /etc/nologin
```
This will prevent anyone other than root from logging in - so since the root account in ubuntu is locked, **no one** will be able to log in until the file is removed again.

Again, you could automate this with cron by adding the following to /etc/crontab:
```
0 20 * * * root touch /etc/nologin
0 8 * * * root rm /etc/nologin
```
This should prevent anyone from logging in between 20:00 at night and 8:00 in the morning. **Be very careful** though, because if something goes wrong, you'll be locked out of your own machine.

For example, if a power failure prevented the cron job for removing from running, your only option would be to boot into recovery mode and manually delete the nologin file.

---

### Post by nothingspecial on 2009-03-09
Have a look at [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=887769")

---

### Post by 3pinner on 2009-03-09
> **nothingspecial said:**
> Have a look at [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=887769")

Thank you!
Thats exactly what I need!

---

