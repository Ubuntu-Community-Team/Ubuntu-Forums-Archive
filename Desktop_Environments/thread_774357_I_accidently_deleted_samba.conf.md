---
title: "I accidently deleted samba.conf"
date: 2008-04-29
forum: Desktop Environments
---

### Post by sheepscrossing on 2008-04-29
I accidently deleted samba.conf from my new 8.04 Ubuntu last night.
I uninstalled and reinstalled Samba but the /etc/samba directory wasn't refreshed.  Does anyone know how to get the conf file back without reloading Ubuntu?  Thanks!!

---

### Post by patis on 2008-04-29
Have you tried the command "sudo dpkg-reconfigure samba"?

---

### Post by sheepscrossing on 2008-04-29
Thanks, but that didn't work unfortunately -  it returned the following error:    samba is broken or not fully installed
  Using Synaptic to remove and reinstall won't work either.  If I try to completely remove Samba common it asks if I want to remove the Ubuntu desktop also..........   The answer to that is NO...

---

### Post by Zorael on 2008-04-29
ubuntu-desktop is a metapackage "bundle" that refers to a whole bunch of packages (Gnome, all the standard programs, Samba; whatever is there when you've just installed). Removing a part of that bundle will "break" ubuntu-desktop, but it's safe to do. You won't hose your system.

I'd try aptitudes reinstall option.
```
$ sudo aptitude reinstall samba smbfs smbclient
```

---

### Post by warbread on 2008-04-30
Do a 
```
:-$ sudo touch /etc/samba/samba.conf
```

... and follow [this link]("http://www.flatmtn.com/article/setting-samba"), then copy and paste the example.

Would that help?

---

### Post by sheepscrossing on 2008-04-30
Thanks Warbread - I think that will do the trick!

---

### Post by sheepscrossing on 2008-04-30
Thanks, Zorael - I think that your post and the one from warbread will get me back on track!

---

### Post by sheepscrossing on 2008-04-30
> **Zorael said:**
> ubuntu-desktop is a metapackage "bundle" that refers to a whole bunch of packages (Gnome, all the standard programs, Samba; whatever is there when you've just installed). Removing a part of that bundle will "break" ubuntu-desktop, but it's safe to do. You won't hose your system.

I'd try aptitudes reinstall option.
```
$ sudo aptitude reinstall samba smbfs smbclient
```

Just to be clear - the file that I accidently deleted was smb.conf, not samba.conf....  Samba wouldn't configure and start the daemons until I changed the file name.  Thanks to Warbread and Zorael for their help.

---

