---
title: "Enabling Core Dumps"
date: 2009-06-11
forum: General Help
---

### Post by Shoie13 on 2009-06-11
I've googled the issue and tried every solution known to man, but I cannot enable core dumps on my Debian 5.0.1 system. I've tried using ulimit but I receive the error below. I don't see any limitations in the /etc/profile or the /etc/skel folder, and I'm pretty sure all the necessary modifications have been done to /etc/security/limits.conf and the pam.d file, but at this time I can't remember what exactly I did to them so if necessary to recheck, please ask me to do so. I don't want some type of work around, because I need core dumps enabled for the program I am running. I have root access, so thats not a problem. Thank you in advance.

```

shoie13@swgi:~/swgi/src$ ulimit -c unlimited
-bash: ulimit: core file size: cannot modify limit: Operation not permitted
shoie13@swgi:~/swgi/src$ 

```

---

### Post by lamego on 2009-06-11
You probably have a system imposed limits (which are not set on Ubuntu, but eventually on Debian):
Please check:
/etc/security/limits.conf

You will need to reboot for the change to take effect.

---

### Post by Shoie13 on 2009-06-11
> **lamego said:**
> You probably have a system imposed limits (which are not set on Ubuntu, but eventually on Debian):
Please check:
/etc/security/limits.conf

You will need to reboot for the change to take effect.

[quote=Shoie13]and I'm pretty sure all the necessary modifications have been done to /etc/security/limits.conf[/quote]

At one point, I had the dumps working and upon another reboot, ulimit would not allow me to set them again, so apparently something reverted, however.

Here is the limits.conf file:
```

#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
*                soft    core            1000000    
*                hard    core            unlimited

# End of file

appAdmin soft    nofile          8000
appAdmin hard    nofile          8000

```

---

