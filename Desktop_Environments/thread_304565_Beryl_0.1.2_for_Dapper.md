---
title: "Beryl 0.1.2 for Dapper"
date: 2006-11-22
forum: Desktop Environments
---

### Post by azidrane on 2006-11-22
The SVN on the beryl wiki isn't working for dapper right now, and I've never had it working so who knows.
Does anyone have a repo for the beryl 0.1.2 release for dapper? I've tried downloading the dep's but they just won't install... I'm getting dependancy issues where libemerald0 won't install until emerald is installed, but that deb won't load because it conflicts with "emerald" it's just wierd...

Anyway, I've got this working on my edgy box, but my laptop has an ati card and won't work with the new xorg in edgy (only runs xgl) so i run dapper, xgl, beryl. Works great on 0.1.1 (but i want the burn!!!)

cheers!

---

### Post by ingo on 2006-11-22
have you tried this? it got beryl installed if nothing else...

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

my prob is that the window decorations disappear as soon as I switch to beryl :(

---

### Post by azidrane on 2006-11-23
That walkthrough installs beryl 0.1.1 from the main Repo, but it doesn't install the newest builds (0.1.2 1342 now i think). The SVN is working for my Edgy box but not for my dapper box. When i do a apt-get update on my dapper box i get this error.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/Release](http://3v1n0.tuxfamily.org/dists/dapper/Release) Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As for your window decorations disapearing, I had the same problem, but I've forgotten what the fix was...

---

### Post by azidrane on 2006-11-23
I found the answer. DL the new packages here in a tarball:
[http://rapidshare.com/files/4391064/beryl-svn-1369mc-dapper.tar.gz.html](http://rapidshare.com/files/4391064/beryl-svn-1369mc-dapper.tar.gz.html)

DL the tar to the desktop
open terminal
cd Desktop/beryl-svn-*
sudo dpkg -i *.deb

turn off beryl (set metacity to widnow manager and then close beryl)
relaunch beryl (type beryl-manager at terminal or alt+F2)
set beryl as manager and Voila!

Cheers!

P.S. Keep up to date on this forum ([http://forum.beryl-project.org/topic-6523-3.html)](http://forum.beryl-project.org/topic-6523-3.html)). thanks to user esential

---

### Post by CtrlAltDelete on 2006-11-25
I am an uber noob...I went to the forum downloaded Beryl-Dapper-svn-1210.tar.gz and placed it on my desktop

Next i tried cd Desktop/beryl-svn-*

and it finds nothing?

---

### Post by ingo on 2006-12-01
tar.gz files are compressed. you need to untar them (right click or on command line).

---

### Post by Castar on 2006-12-02
> **ingo said:**
> have you tried this? it got beryl installed if nothing else...

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

my prob is that the window decorations disappear as soon as I switch to beryl :(

Don't you also need to run emerald? I had the same problem, run emerald and the window decorations will come up, as kwin and metacity do not work with beryl.

---

### Post by SingLee on 2006-12-03
I still got this error. I'm wondering if upgrading 0.1.3 is worth it?

---

### Post by telperion on 2006-12-12
Check here for update:
[http://forum.ubuntu-it.org/index.php?topic=45451.msg241885#msg241885](http://forum.ubuntu-it.org/index.php?topic=45451.msg241885#msg241885)

---

