---
title: "how to disable updatedb"
date: 2009-06-04
forum: General Help
---

### Post by fraktalek on 2009-06-04
Hi,

how do I disable updatedb in Jaunty?

I got rid of trackerd by unistalling it...should I do the same with updatedb? I know it's run by cron but don't wanna mess with it, would prefer some simple, user-friendly and system-friendly off switch.

---

### Post by jowilkin on 2009-06-04
Well it's run by a file called /etc/cron.daily/mlocate.  So an easy way to disable it would be to delete that file, but since then you couldn't undo the action it would probably be better to move it to some other place like your home directory.  So a terminal command like the following would do that ```
sudo mv /etc/cron.daily/mlocate ~
```

Why do you want to do this though?  locate is a very useful command IMO and after the first time updatedb runs, it runs very quick and doesn't use much resources.

If you want to completely remove the package owning it, you can find out what package owns a file with dpkg -S, like ```
jowilkin@myth ~ $ dpkg -S /etc/cron.daily/mlocate
mlocate: /etc/cron.daily/mlocate
```

So you would remove the mlocate package to prevent this behavior with ```
sudo aptitude remove mlocate
```

---

### Post by zipizap on 2011-06-21
This post is quite old, but still I'll leave this info for anyone that comes by

> **fraktalek said:**
> Hi,

how do I disable updatedb in Jaunty?

I got rid of trackerd by unistalling it...should I do the same with updatedb? I know it's run by cron but don't wanna mess with it, would prefer some simple, user-friendly and system-friendly off switch.

To disable any of the scripts in
```
/etc/cron.weekly
/etc/cron.hourly
/etc/cron.daily
/etc/cron.monthly
```
you can simply make the script not-executable (this way you can always make it executable again to reenable it)

For example, to disable /etc/cron.daily/mlocate, do:
```

sudo chmod -x /etc/cron.daily/mlocate

```To renable it, you can simply
```

sudo chmod +x /etc/cron.daily/mlocate

```
Cheers

---

