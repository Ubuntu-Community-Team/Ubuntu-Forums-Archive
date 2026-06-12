---
title: "firefox 1.5 problems"
date: 2005-12-08
forum: General Help
---

### Post by devwild on 2005-12-08
I installed the binaries of firefox 1.5 in /opt and have been using it ok, however every time it tries to open a save/open dialog, it hangs. Has anyone else been having this problem? is there a fix because this is pretty critical. :)

---

### Post by jrib on 2005-12-08
there is a file on firefox's bugzilla filed about this I believe

I don't have the problem everytime I try it but happens sometimes.

---

### Post by newuser111 on 2005-12-08
i assume you did it using the instructions posted here?

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

i think the problem is caused by not giving the firefox directory user permissions

 sudo chown -R username:username /opt/firefox

that page said it was a bad idea to run firefox this way, but i dont see how, because by default firefox is installed on ubuntu with the user permissions, giving the whole directory user permission seems safe enough, its not as if you are running firefox as root

btw firefox 1.5 + fasterfox addon is the fastest browser for linux easily

---

### Post by rwabel on 2005-12-08
[quote=newuser111]i assume you did it using the instructions posted here?

[https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

i think the problem is caused by not giving the firefox directory user permissions

 sudo chown -R username:username /opt/firefox

that page said it was a bad idea to run firefox this way, but i dont see how, because by default firefox is installed on ubuntu with the user permissions, giving the whole directory user permission seems safe enough, its not as if you are running firefox as root

btw firefox 1.5 + fasterfox addon is the fastest browser for linux easily[/quote]

I've to disagree. at least for me, opera is much faster than firefox. I've firefox in my home dir and therefore by default user permission and I get the same error. It hangs for a while, not forever.

---

### Post by towsonu2003 on 2005-12-08
[QUOTE=devwild]I installed the binaries of firefox 1.5 in /opt and have been using it ok, however every time it tries to open a save/open dialog, it hangs. Has anyone else been having this problem? is there a fix because this is pretty critical. :)[/QUOTE]
this is a known bug in firefox bugzilla... although I dont remember the bug #, I know it will be fixed with the next update. You could also try searching the firefox bugzilla and/or use one of the nightly builds (which are for development use).

---

