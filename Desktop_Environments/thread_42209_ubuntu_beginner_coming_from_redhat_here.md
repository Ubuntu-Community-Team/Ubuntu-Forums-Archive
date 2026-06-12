---
title: "ubuntu beginner coming from redhat here"
date: 2005-06-16
forum: Desktop Environments
---

### Post by s0lid on 2005-06-16
hi guys just need tips how to config some things it's a bit different from redhat.

how do i set the interface of eth0 manually in redhat there's netconfig or manually edit /etc/sysconfig/network-scripts/ifcfg-eth0 and also the default network where should i put it?

another question is how can i change the runlevels of the services like apache postfix ssh to run on runlevel 3 4 and 5. in redhat you can do this by the command of chkconfig.

---

### Post by defkewl on 2005-06-16
> how do i set the interface of eth0 manually in redhat there's netconfig or manually edit /etc/sysconfig/network-scripts/ifcfg-eth0 and also the default network where should i put it?
/etc/networks/interfaces

> another question is how can i change the runlevels of the services like apache postfix ssh to run on runlevel 3 4 and 5. in redhat you can do this by the command of chkconfig.
update-rc.d {service-name} defaults

---

### Post by s0lid on 2005-06-17
hmmm... update-rc.d confuse me.

what's the command in ubuntu to say run postfix in runlevel 345 in RH it's chkconfig postfix on or chkconfig --runlevel 345 postfix on

---

### Post by intangible on 2005-06-18
[QUOTE=s0lid]hmmm... update-rc.d confuse me.

what's the command in ubuntu to say run postfix in runlevel 345 in RH it's chkconfig postfix on or chkconfig --runlevel 345 postfix on[/QUOTE]
 Seems like you need the new tool someone is working on called "BUM" [http://ubuntuforums.org/showthread.php?t=42129](http://ubuntuforums.org/showthread.php?t=42129)

---

