---
title: "Synaptic cannot determine display-device"
date: 2012-02-28
forum: Desktop Environments
---

### Post by hamiljf on 2012-02-28
Running Gnome Classic in Ubuntu 11.10 I've been using synaptic without trouble.  Just today, it won't run and I think this is the problem...

pkexec	pam_ck_connector(polkit-1:session): cannot determine display-device
Executing command [USER=root] [TTY=unknown] [CWD=/home/hamiljf] [COMMAND=/usr/sbin/synaptic]

I could well have diddled with some setting between now and the last time I used synaptic so something could have changed, or some update could have been installed and messed up, but I have no idea what.

Ideas to fix anyone ?

---

### Post by jobsdev on 2012-05-26
Same here, but only when having an nxserver client session opened.

```
pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
```Tried with xubuntu 12 and today installed lubuntu-desktop, but no change, yet. Will provide more details next days. I guess, that other programs are affected, too - crashes happen very often.

Because your posts is quite old, do you remember if you we're using remote session or anything of this kind, like I do with nxserver?  Please see [http://en.wikipedia.org/wiki/NX_technology](http://en.wikipedia.org/wiki/NX_technology) for more details.

---

