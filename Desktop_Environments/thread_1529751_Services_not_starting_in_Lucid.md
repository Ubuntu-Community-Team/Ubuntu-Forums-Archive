---
title: "Services not starting in Lucid"
date: 2010-07-12
forum: Desktop Environments
---

### Post by NateTut on 2010-07-12
I have been searching for a while but I can't figure this one out. Basically services aren't starting up, like cron, VBox, ssh. I suspect a problem in the boot process, but I don't know where to look for errors with init or upstart or whatever it is these days.

Thanks for the help

---

### Post by Peepsalot on 2010-07-13
I'm having similar problems.  Some of my services are starting, but not all of them.  For example, ssh and samba start fine, but apache2, cups, and boinc-client are not starting.

These were all working fine just days ago, but when I restarted today they did not come up.  I am able to start them manually for example with 
```
sudo /etc/init.d/apache2 start
```

---

### Post by NateTut on 2010-07-13
I wonder if an update broke something? Probably unrelated, but my insert key isn't working as expected either...

---

### Post by TMcC on 2010-07-15
This seems to be due to there being a race condition in the 'upstart' package, where multiple scripts are racing to get access to '/dev/console'. When one fails, it just aborts instead of carrying on.

A work around is this (see: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/587079]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/587079") and [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506"))

Basically, the workaround stops the scripts from asking for console access, and adds a dependency that waits for rsyslog to start before any of the /etc/rc2.d init scripts run.

```
sudo -s
for file in /etc/init/*.conf; do sed -i 's/^console output/\#console output/' $file; done
sed -i 's/start on filesystem and net-device-up IFACE=lo/start on filesystem and started rsyslog and net-device-up IFACE=lo/' /etc/init/rc-sysinit.conf
sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="init='\''\/sbin\/init --verbose'\''"/' /etc/default/grub
update-grub

```

The grub line is just to add some extra debug to see if anything fails, and can be omitted.

If you cut-and-paste the above, do the 'sudo -s' line first, followed by the rest. Obviously the grub stuff won't work if you've altered the GRUB_CMDLINE_LINUX from its "" default.

Numerous reboots seem to show that it's working ok; prior to this I would end up with an undefined run level as reported by the 'runlevel' command, and rc2 scripts wouldn't execute.

---

### Post by BobvanderPoel on 2010-08-09
Thanks for this. I've applied the suggested changes ... hopefully options like cups, etc. will now load all the time :)

As an added suggestion, if you add things to /etc/rc.local make sure to either change the first line from "#!/bin/sh
-e" to "#!/bin/sh" (remove the -e). If anything is printed to the console by your rc.local program it will be considered to be an error and abort the rest of the script. IMHO, a dumb way for Ubuntu to do this.

Okay, maybe I'm wrong on this ... but my "fix" solves the problems I was having.

---

### Post by mwildam on 2010-08-10
> **Peepsalot said:**
> These were all working fine just days ago, but when I restarted today they did not come up.  I am able to start them manually for example with 
```
sudo /etc/init.d/apache2 start
```
And this BTW is depreceated with Lucid, use
```
service apache2 start
```
or even better
```
start apache2
```
instead.

---

