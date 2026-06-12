---
title: "Nautilus Error"
date: 2009-02-26
forum: General Help
---

### Post by akh00 on 2009-02-26
I don't have much time so I'll cut it short. This is the error I got this morning when I tried to mount a drive in Ubuntu 8.04:

```
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.
```

I know restarting will fix it, but can anyone tell me why I got it in the first place? Thank you.

---

### Post by T.J. on 2009-02-27
Bonobo is a component of GNOME that has been around for a long time.  They are working to actually remove it from GNOME last I heard.

Sadly, Nautilus having issues is not unheard of.  You can read more here, if you are interested: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/128776](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/128776).  It appears to be similar to your problem.

If you are still having problems, I'd try (drop the quotes):

"sudo aptitude update"

then

"sudo aptitude reinstall nautilus"

in your terminal.  That will reinstall nautilus.  It may belp.

---

