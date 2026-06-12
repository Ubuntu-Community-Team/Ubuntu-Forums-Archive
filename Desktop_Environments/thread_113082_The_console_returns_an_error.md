---
title: "The console returns an error"
date: 2006-01-05
forum: Desktop Environments
---

### Post by antubis on 2006-01-05
When I install something with apt-get the console retuns this error:

> 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "bg_BG:bg",
        LC_ALL = (unset),
        LANG = "bg_BG.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").


What this error can be and how can I fix it?
Thanks to all.

---

### Post by kairu0 on 2006-01-05
First, do:

```
sudo dpkg-reconfigure locales
```

to make sure that your locale is installed. If it is not, check it in the list and push OK.

---

### Post by Co.Sinecure on 2006-01-14
For some reason, dkpg-reconfigure doesn't seem to exist for me...?

I cleared up the locale errors by using:

[FONT="Courier New"]
> sudo locale-gen
> sudo apt-get -f dist-upgrade
[/FONT]

---

