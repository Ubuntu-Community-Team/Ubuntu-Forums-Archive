---
title: "samba fails to start"
date: 2005-12-14
forum: Desktop Environments
---

### Post by coldwater on 2005-12-14
i can't access my brother's XP box, and he can't access my ubuntu. it worked until a couple of days ago, and i can't remember changing anything related to samba. tried a couple of things but then i noticed samba isn't running. i tried:

sudo /etc/init.d/samba start

but all i got was:

 * Starting Samba daemons..                                              [fail]

tried to reinstall samba, but to no avail. the question is, how do i find out what's wrong?

---

### Post by harisund on 2005-12-14
Well.. that did happen to me once, and what I did was simply copy the samba configuration file (I think in /etc/samba/smb.conf or something close) and then

apt-get --purge remove samba smbfs

and again
apt-get install samba smbfs

And copied the configuration files back and
/etc/init.d/samba stop
/etc/init.d/samba start

And restarted the Windows machine (though I don't think you need to do this) and it worked. 

Did you try the same thing? 

(Note: You would need sudo everywhere.)

---

### Post by coldwater on 2005-12-14
tried it just now. no good. won't start. thanks anyway ;)

---

### Post by schilcha on 2005-12-14
Have a look at your log-files to just get an idea of what's going wrong. (Don't know where they are exactly with ubuntu... try /var/log/samba/, /var/log/daemon.log or any of those files in /var/log)

I don't have a samba-server installed, but I can perfectly access windows-shares. For this direction, a running samba service is abviously not necessary.

---

### Post by coldwater on 2005-12-14
thanks, that's what i was looking for.  this is the problem line in /var/log/samba/log.smbd:

[2005/12/14 18:36:37, 1] auth/auth_util.c:make_server_info_sam(840)
  User guest in passdb, but getpwnam() fails!

i deleted (or commented-out) all guest related stuff in my /etc/samba/smb.conf - i don't need 'em anyhow, and voila! only i don't know what made samba crash, i definitely did not change any samba configuration in past two weeks or so.. but hey, it's working :)

thanks schilcha!

---

