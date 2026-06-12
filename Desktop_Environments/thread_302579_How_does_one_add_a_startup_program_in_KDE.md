---
title: "How does one add a startup program in KDE?"
date: 2006-11-18
forum: Desktop Environments
---

### Post by drummer4lifex on 2006-11-18
Hello,

I've normally been a Gnome user, but I decided to try KDE. I installed beryl and I'm wondering how I would go about adding beryl-manager to load on my session. This is Kubuntu 6.10 by the way. 

Thanks

---

### Post by mexlinux on 2006-11-18
Put any program or link you want in this folder:
~/.kde/Autostart/

---

### Post by FyreBrand on 2006-11-18
To make this work in KDE this is the link needed.
```
$ ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager
```
I believe this enables the beryl-manager for all sessions.

I found this on this Install for Beryl/XGL on the beryl wiki.  Here is the page: [**Install/Ubuntu/Edgy/XGL - Beryl Wiki**]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL").

That HowTo explains how to add an XGL session option.  There is a way to add beryl-manager only to that XGL session.  It links to a gentoo beryl script page.  I'm not that experienced yet so I haven't figure out how to translate the scripts to work in Kubuntu.

If you figure out and test a script to make this run only in an XGL session please post your fix.

I'm not using the global start and will wait until I can figure out an XGL only session start for beryl.

---

