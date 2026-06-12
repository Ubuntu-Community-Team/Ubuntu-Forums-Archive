---
title: "kdesu broken"
date: 2006-03-07
forum: Desktop Environments
---

### Post by Dingo_aus on 2006-03-07
I always get this error when trying to execute kdesu

kdesu: WARNING: Daemon not safe (not sgid), not using it.

Any ideas? 
Could I reinstall the package with kdesu to fix it? Which package is it in?

Thanks,

Nigel

---

### Post by Dingo_aus on 2006-03-07
Can anyone help me with this? - kdesu being broken prevents me running anything in KDE with root privileges.

From what I've read the daemon has to be started very specifically or it would be a huge security risk. Obviously it can't start up the way it wants.

Anyone got any tips on what might be causing the failure of the kdesu daemon properly?

---

### Post by retsaw on 2006-03-09
Don't know what might be causing it, but kdesu seems to be in the kdebase-bin package and you can reinstall it with ```
sudo apt-get install --reinstall kdebase-bin
```HTH

---

### Post by Dingo_aus on 2006-03-10
The solution is found from my own stupidity.

I had accidently recursively overwritten the suid of the sudo file upon which kdesu relies.

The solution is the bring up a console
login as root
navigate to the /usr/bin/ directory.
then use chmod like this:

chmod a+s sudo

this should then allow kdesu to work again.

It was my solution.

---

