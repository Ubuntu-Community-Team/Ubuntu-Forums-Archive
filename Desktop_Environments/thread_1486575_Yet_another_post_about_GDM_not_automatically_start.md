---
title: "Yet another post about GDM not automatically starting..."
date: 2010-05-18
forum: Desktop Environments
---

### Post by thecgmguy on 2010-05-18
Ubuntu 10.04

Hi guys. I'm not sure why but quite recently, my ubuntu desktop started bringing up the command prompt login screen after booting. I want GDM to start up by default.

I can manually bring up GDM by typing:

sudo service gdm start

or

sudo /usr/sbin/gdm

but I want something more permanent.

The contents of /etc/X11/default-display-manager point to /usr/sbin/gdm

The chkconfig status for GDM shows that it's off on all run levels... could that be it? I tried running:

sudo chkconfig --add gdm 

and just got errors..."The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs"

I've tried running dpkg-reconfigure gdm but nothing seems to happen and it just returns me to the prompt (no errors). 

Any ideas? How can I get GDM to automatically come up again? Any/all help is appreciated!

-M

---

### Post by anglican on 2010-05-18
> **thecgmguy said:**
> Ubuntu 10.04

Hi guys. I'm not sure why but quite recently, my ubuntu desktop started bringing up the command prompt login screen after booting. I want GDM to start up by default.

I can manually bring up GDM by typing:

sudo service gdm start

or

sudo /usr/sbin/gdm

but I want something more permanent.

The contents of /etc/X11/default-display-manager point to /usr/sbin/gdm

The chkconfig status for GDM shows that it's off on all run levels... could that be it? I tried running:

sudo chkconfig --add gdm 

and just got errors..."The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs"

I've tried running dpkg-reconfigure gdm but nothing seems to happen and it just returns me to the prompt (no errors). 

Any ideas? How can I get GDM to automatically come up again? Any/all help is appreciated!

-M
Starting gdm is managed by "[COLOR=Red]upstart[/COLOR]", the configuration file is /etc/init/gdm.conf. For what it's worth, the command to change the status of a service with chkconfig is e.g.
```
sudo chkconfig --level 2345  <service> on

```Which would turn on <service in run levels 2 3 4 and 5 - but this wont work for anything run by "[COLOR=Red]upstart[/COLOR]" **such as gdm** where the configuration files are in /etc/init.

H

---

