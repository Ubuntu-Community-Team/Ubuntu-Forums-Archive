---
title: "Starting turboprint daemon to start automatically"
date: 2009-04-15
forum: General Help
---

### Post by MadEgg on 2009-04-15
I have a Canon Pixma iP4600 printer and I have bough a TurboPrint license for it to be able to use all its features. TurboPrint comes with a daemon which monitors the printer status.

I want this daemon to start automatically. The .deb package installed a rc-script into /etc/init.d/tpdaemon to start it.

When I manually enter:
```

sudo /etc/init.d/tpdaemon start

```

on a console, this works. But I cannot get it to start automatically. I have put symlinks in the appropriate directories (I think) but it still does not start. The links I have in place are:

```

/etc$ ll /etc/rc?.d/S92tpdaemon
lrwxrwxrwx 1 root root 18 2009-04-06 22:24 /etc/rc2.d/S92tpdaemon -> ../init.d/tpdaemon*
lrwxrwxrwx 1 root root 18 2009-04-06 22:25 /etc/rc3.d/S92tpdaemon -> ../init.d/tpdaemon*
lrwxrwxrwx 1 root root 18 2009-04-06 22:26 /etc/rc4.d/S92tpdaemon -> ../init.d/tpdaemon*
lrwxrwxrwx 1 root root 18 2009-04-06 22:26 /etc/rc5.d/S92tpdaemon -> ../init.d/tpdaemon*

```

I also tried using BUM but somehow it does not show the tpdaemon script at all so I cannot enable it. How should I fix this?

---

### Post by aktiwers on 2009-04-15
I think you could put 
```
sudo /etc/init.d/tpdaemon start
```

at the end of our  /etc/rc.local file.

Im not sure, try it out :)

---

### Post by MadEgg on 2009-04-16
I suppose that would work but it's not a really elegant solution. The rc-scripts are supposed to be able to started automatically without using rc.local as far as I know, but somehow it doesn't work here.

Anyway, this is a good workaround for the time being.

---

### Post by MadEgg on 2009-04-19
Hmm, I added it to /etc/rc.local but it still does not get started. Even though rc.local is executable and added to all runlevels. Maybe it depends on something not started when rc.local is executed? Is the output from rc.local logged somewhere? I cannot find it anywhere in /var/log, except for the auth.log but that is the result from each sudo command I enter to start the daemon manually.

---

### Post by Yettie on 2009-05-12
I got it to start automatically by adding a command ( /etc/init.d/tpdaemon start ) to the Startup Applications.


For anyone who needs exact instructions:

Go to System/Preferences/Startup Applications (or Sessions in Intrepid) and add the following startup program -

Name = Turboprint Daemon
Command = /etc/init.d/tpdaemon start

---

