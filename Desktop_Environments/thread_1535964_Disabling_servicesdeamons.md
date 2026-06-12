---
title: "Disabling services/deamons"
date: 2010-07-21
forum: Desktop Environments
---

### Post by amsterdamharu on 2010-07-21
I see stuff like samba, nfs-kernel-server, cups and bluetooth are started. Not sure if you'd call it a service or deamon but tried to disable them by renaming the sym links in /etc/rc[number].d

I use nfs ocasionally and would like to start this service manually. Renaming seems to work but then I found out that portmap is still running. Could not find a portmap script in /etc/rc... so now I'm wondering if there is one place where these kinds of services are started and maybe there if there is a gui available for it like in Hardy?

Using ubuntu 9.10

---

### Post by cbowman57 on 2010-07-21
Have you tried rcconf?

---

### Post by amsterdamharu on 2010-07-21
Thank you for your reply.

rcconf might be a bit outdated since it didn't seem to work. It created script in etc/rc[number].d but since it seems upstart is handling starting this deamon it doesn't do much

---

### Post by ajgreeny on 2010-07-21
You can stop some services with **bum** (**B**oot**U**p**M**anager) which you can install from the repos, but unfortunately not all.  I have no idea about nfs, but you can certainly stop bluetooth that way, and you can even stop some things in **System ->Preferences ->Startup Applications**.  I think rc-conf has now been deprecated for a lot of things, and though they may be listed, they can not be stopped or started using it any more.

You can also try the command ```
sudo service <name> stop
``` using the name of the service you want to stop where I show <name>.  As an example ssh can be stopped that way, so if you have ssh-server installed but only use it very occasionally, you can add the command server ssh stop to the **/etc/.rc.local** file and it will stop ssh at bootup, then when you want to use it, use command ```
sudo service ssh start
```
The same command may work for a great many different services, but I have not tried, so will leave it to you to experiment further.

---

### Post by amsterdamharu on 2010-07-21
Hi greeny, thanks for your reply. I can stop the service with the service command but I would like the service to never start. So the /etc/rc[number].d symlinks work quite well for nfs, samba, bluetooth and saned but somehow portmap is not started this way (maybe I forgot to run update-rc.d will try again). Here is all the portmap I could find:
```
>sudo find /etc -name '*portmap*'
/etc/init/portmap.conf
/etc/rc4.d/K20portmap
/etc/rc1.d/K20portmap
/etc/rc3.d/K20portmap
/etc/default/portmap
/etc/rc0.d/K20portmap
/etc/rc6.d/K20portmap
/etc/rc2.d/K20portmap
/etc/rc5.d/K20portmap
/etc/init.d/portmap

```

Now ran the update-rc.d and  ```
sudo update-rc.d portmap disable
``` will reboot and see what happens.

---

### Post by mikewhatever on 2010-07-21
There is a program called BUM in the repositories, does exactly what you want.

---

### Post by sisco311 on 2010-07-21
Take a look at:
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)
and
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

To disable portmap from being started at bootup, you could edit the /etc/init/portmap.conf file to something like:
```
# portmap - RPC port mapper

# Portmap is a server that converts RPC (Remote Procedure Call) program
# numbers into DARPA protocol port numbers. It must be running in order
# to make RPC calls.

description     "RPC port mapper"
author          "Steve Langasek <steve.langasek@canonical.com>"

start on ([B]start-portmap
          and[/B] virtual-filesystems
          and net-device-up IFACE=lo)

expect fork
respawn

script
...

```
and start portmap with:
```
sudo initctl start portmap
```
or
```
sudo initctl emit start-portmap
```

P.S. Writing in uppercase means that you yell and it's considered rude. ;)

---

### Post by amsterdamharu on 2010-07-21
Hi sisco, thanks for the info. It looks like some deamons/services are started/disabled by init scripts and some by upstart. The autostart scripts are installed by the deb file I assume.

Changed the portmap.conf, rebooted and portmap is not started.
```
sudo service portmap start
```Will start it.

Thank you for all your advice and solving this problem.

---

### Post by sisco311 on 2010-07-21
> **amsterdamharu said:**
> 
As for the caps; it wasn't meant as shouting but it would need to stick out as it is work in progress without getting the thread unnecessarily long. Will change it once the solution is clear.


Oh, okay. :)

> **amsterdamharu said:**
> 
As for bum, I will install that too and see what it does.

update-rc.d and BUM are tools for managing System-V style init script, they are not compatible with Upstart jobs.

---

