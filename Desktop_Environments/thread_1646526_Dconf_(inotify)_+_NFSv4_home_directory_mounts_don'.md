---
title: "Dconf (inotify) + NFSv4 home directory mounts don't work in Ubuntu 10.10"
date: 2010-12-16
forum: Desktop Environments
---

### Post by wapsi on 2010-12-16
Hi,

I have noticed that when I have my home directory mounted over network with NFSv4 ==> applications that use dconf to save preferences do not work correctly.

If I try to save preferences they won't save and I'm getting "Unable to contact dconf service" errors with Evince, Empathy etc.

I was googling this issue and I figured out that Dconf uses inotify() ( [http://lwn.net/Articles/403632/](http://lwn.net/Articles/403632/) and [http://lwn.net/Articles/403577/](http://lwn.net/Articles/403577/) ) and those notifys don't work with NFS at all so the whole "dconf thing" doesn't work!

Am I right that Ubuntu is moving from GConf to DConf? If that is true I think this issue will be a serious problem if most of the applications use mechanism to save settings that doesn't work with NFS mounted drives. It is quite common to use NFS to mount home directory in some schools, companies and LTSP-machines.


BTW. I've tried to reinstall dconf and libdconf0 packages with no working result. When I'm using my home directory locally there is no problems.

And with Ubuntu 10.04/9.10/9.04... there were no these problems.

Links:
[http://serverfault.com/questions/1507/how-do-i-get-inotify-like-event-notifications-from-an-nfs-server](http://serverfault.com/questions/1507/how-do-i-get-inotify-like-event-notifications-from-an-nfs-server)
[https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/645448)
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/620733](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/620733)
[http://ww.ubuntuforums.org/showthread.php?t=1581739](http://ww.ubuntuforums.org/showthread.php?t=1581739)

BR,
Wapsi

---

### Post by wapsi on 2010-12-17
Hi,

this bug doesn't appear when mounting home directories with OpenAFS ([http://www.openafs.org/](http://www.openafs.org/)) with krb5/openldap authentication so the problem is with NFSv4.

---

### Post by derlinuxer on 2011-03-08
Hi,

have same problem with NFS and dconf and found a workaround in connection with empathy. Should work with other apps using dconf too.

change the CACHE Path to a non nfs mount area and the start empathy.

like:
export XDG_CACHE_HOME=/export/nonNFS
empathy

I guess the problem is that dconf will do something in the "cache dir" (inside the NFS mount filesystem) with root rights. If the option no_root_squash is set on the NFS Server for this export it will be denied.

default XDG_CACHE_HOME is $HOME/.cache

derlinuxer

---

