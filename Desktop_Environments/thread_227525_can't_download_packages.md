---
title: "can't download packages"
date: 2006-08-01
forum: Desktop Environments
---

### Post by sr243 on 2006-08-01
i just installed kubuntu, and started downloading some programs, but after a restart, i found that i could no longer download packages.

In adept, it only shows packages already installed, and when i try "sudo apt-get update" i get stuff like 

"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 146.137.96.7 80]"

and a "E: Some index files failed to download, they have been ignored, or old ones used instead." at the end.

I obviously have internet, since I'm posting here, and my sources.list looks normal, and being the linux newbie that I am, I have no idea what to do.  Any hints?  Thanks!

---

### Post by taurus on 2006-08-01
Maybe the us.archive.ubuntu.com is down!  Try to remove the "us" in your /etc/apt/sources.list and run it again...

---

### Post by sr243 on 2006-08-01
i pinged us.archive.ubuntu.com and it works fine, so it's not the server's fault...

---

### Post by sr243 on 2006-08-01
i changed around the sources.list file around anyway but it still doesn't work

---

### Post by ButteBlues on 2006-08-01
Try a sudo aptitude update.

If you get a message about not being able to lock/unlock a directory, run:

$ dpkg --configure-a

---

### Post by sr243 on 2006-08-01
i just got more of the same using aptitude


like

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.182 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Connection failed

and

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.182 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Connection failed

Any suggestions?

---

### Post by sr243 on 2006-08-02
ah nevermind, im just going to reinstall the whole thing...though i'm kinda mad because that would make this the 3rd time I have to reinstall because of some problem with the software.

---

### Post by sr243 on 2006-08-02
Okay I found the problem.  Apparently Dapper's apt-get and my Netgear WGT-624 router don't get along well.  Apt works fine without a router, or when I use a linksys router at work, but not with the Netgear at home.

Should this be considered a bug? I believe it worked fine when I used Breezy...

---

