---
title: "kcron installed, error &quot;bash: kcron: command not found&quot;"
date: 2009-02-24
forum: General Help
---

### Post by woody22075 on 2009-02-24
I am running Ubuntu 8.10.  I have installed kcron using synaptic and there were no errors during install.  However, when i type "kcron" into the terminal, I receive a "bash: kcron: command not found" error.  The kcron man page I can access.  I have uninstall and reinstalled kcron to the same effect.  Interestingly, I installed gcrontab.  It runs; however, I get a "no crontab for [user]" in the terminal--this is the same when I run in root.

Any ideas as to what the issue is?  I would really like a graphical cron to use.

Thanks for the help!

M.

---

### Post by snova on 2009-02-24
This is the file listing for kcron:

```

kcron: /usr/lib/kde4/kcm_cron.so
kcron: /usr/share/doc/kcron/AUTHORS
kcron: /usr/share/doc/kcron/README
kcron: /usr/share/doc/kcron/changelog.Debian.gz
kcron: /usr/share/doc/kcron/copyright
kcron: /usr/share/doc/kde4/HTML/en/kcron/common
kcron: /usr/share/doc/kde4/HTML/en/kcron/index.cache.bz2
kcron: /usr/share/doc/kde4/HTML/en/kcron/index.docbook
kcron: /usr/share/doc/kde4/HTML/en/kcron/kcron.png
kcron: /usr/share/doc/kde4/HTML/en/kcron/kcronstart.png
kcron: /usr/share/doc/kde4/HTML/en/kcron/newtask.png
kcron: /usr/share/doc/kde4/HTML/en/kcron/newvariable.png
kcron: /usr/share/doc/kde4/HTML/en/kcron/print.png
kcron: /usr/share/kde4/services/kcm_cron.desktop
kcron: /usr/share/man/man8/kcron.8.gz

```

It doesn't have a program. However, this line is interesting:

```
kcron: /usr/lib/kde4/kcm_cron.so
```

I would guess its interface is somewhere in System Settings.

---

### Post by woody22075 on 2009-02-25
Thanks for the response.  I am rather new to Ubuntu--how do I access System Settings or kcron in this instance?  Thanks again for the assistance,

M.

---

### Post by snova on 2009-02-25
Oh dear, I forgot you're on Ubuntu. System Settings is the central place for Kubuntu configuration, so you might not even have it...

Well, first make sure the 'systemsettings' package is installed. Then it should hopefully be in the menu somewhere. (If you can't find it, Alt-F2 and type in 'systemsettings').

It should be under the Advanced Tab, "Task Scheduler".

---

