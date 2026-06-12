---
title: "Dansguardian upgrade incomplete"
date: 2009-05-05
forum: General Help
---

### Post by ecowan on 2009-05-05
Adept-updater just tried to update DansGuardian, but the configuration step failed. Now my home network is not working properly, and I have a teenage grandaughter who wants to surf.

I tried uninstall and install again, but this is what the details log shows:
```
Selecting previously deselected package dansguardian.
(Reading database ... 178158 files and directories currently installed.)
Unpacking dansguardian (from .../dansguardian_2.9.9.7-2~hardy2_i386.deb) ...
Setting up dansguardian (2.9.9.7-2~hardy2) ...

Configuration file `/etc/dansguardian/dansguardian.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** dansguardian.conf (Y/I/N/O/D/Z) [default=N] ? dpkg: error processing dansguardian (--configure):
 EOF on stdin at conffile prompt
Errors were encountered while processing:
 dansguardian

```

I tried "dansguardian --configure (previous config file)" but that found another error.

I see a couple of files that seem to be left from the install attempt, dansguardian.conf.dpkg-new and dansguardian1.conf.dpkg-new.

Help! 

Thanks. - Erny

---

### Post by ecowan on 2009-05-06
I just tried 
- uninstall dansguardian
- delete /etc/daansguardian (after taking a copy)
- install dansguardian
but somehow he (dpkg?) knows that the previous version of /etc/dansguardian/dansguardian.conf was deleted. Anyhow it still fails at the config step.

Now I am getting worried. - Erny

---

### Post by ecowan on 2009-05-08
So I finally have dansguardian back, after _many_ attempts at deleting, reinstalling, running various scripts and dpkg -configure and copying files from my belated backup.

The secret was to use synaptic to do a complete removal. (I reinstalled, just so synaptic would have something to do.)
I rebooted, again just to be sure.
I installed, using adept. Oddly, he still complained, something about permissions on /var/log/dansguardian, which _were_ 'dansguardian', as he seemed to want. He also wanted me to edit 'dansguardian.conf', of course. Then he said 'Rerun this script'. But what/where is 'this script'?

So I edited dansguardian.conf, commented out the 'UNCONFIGURED' line, copied my personalized exception... and banned... lists from my backup to the new /etc/dansguardian/lists directory, and did 'dansguardian -restart'.

Everything's back and working.

- Erny

---

