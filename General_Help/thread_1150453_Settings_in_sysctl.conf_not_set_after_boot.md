---
title: "Settings in sysctl.conf not set after boot"
date: 2009-05-06
forum: General Help
---

### Post by street spirit on 2009-05-06
Hi.

I have the following custom settings in my /etc/sysctl.conf:

```
kernel.shmmax = 536870912
vm.overcommit_memory = 2
```

At the last reboot, the postmaster didn't come up, complaining that SHMMAX was set too low. Sure enough,

```
$ cat /proc/sys/kernel/shmmax 
33554432
$ cat /proc/sys/vm/overcommit_memory 
0
```

After this

```
sudo sysctl -p /etc/sysctl.conf
```

it worked as intended. I thought the adjustments in /etc/sysctl.conf would automatically be set at boot. Do I have to do anything special to ensure that?

There's nothing in /etc/sysctl.d to overwrite the settings. One possible reason is that /etc/sysctl.conf is symlinked to a file in my (user's) local svn repository.

---

### Post by Brandon Williams on 2009-05-12
One possible explanation is that /etc/sysctl.conf is not considered readable (for some reason) when /etc/init.d/procps is run at startup. If it's not readable, then it won't be activated.

First, instead of running 'sudo sysctl -p', trying running 'sudo /etc/init.d/procps start'. Does this work? If not, then you've got to fix the file so that it 'if [ ! -r /etc/sysctl.conf ]' will fail (i.e. /bin/sh must decide that the file is readable). If it does work, then there's some other more difficult to diagnose issue that only happens at boot time.

It may be the case that your user's SVN repo location is not available yet at the point in the boot process when /etc/init.d/procps is run. You may have to move the file to the root partition in order to ensure that it's available when needed during boot.

---

### Post by street spirit on 2009-05-12
> **Brandon Williams said:**
> First, instead of running 'sudo sysctl -p', trying running 'sudo /etc/init.d/procps start'. Does this work?

Yes, that works.

> **Brandon Williams said:**
> It may be the case that your user's SVN repo location is not available yet at the point in the boot process when /etc/init.d/procps is run. You may have to move the file to the root partition in order to ensure that it's available when needed during boot.

Yeah, you're right. I just tried it out: sysctl.conf symlinked to a location on the root partition works, so it can't be the symlink alone. I'm not very familiar with the boot process in Ubuntu, but my guess is that sysctl.conf is read before other partitions like /home are mounted or otherwise "available" (makes me wonder what would happen if /etc were on a different partition).

I'm using links to files in my SVN repository in a lot of places, because the more systems I've got, the less I can remember all their quirks and special needs... I'll just check out that part of the repo to the root partition then.

Thanks for your help!

---

### Post by Brandon Williams on 2009-05-12
I just took a look in /etc/rcS.d/, and yes ... procps runs with priority 17 and mountall.sh runs with priority 35, so procps will run and attempt to apply sysctl settings before filesystems are mounted. In fact, it runs while the root filesystem is still mounted in read-only mode.

---

