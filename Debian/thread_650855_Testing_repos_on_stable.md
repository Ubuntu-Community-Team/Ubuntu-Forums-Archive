---
title: "Testing repos on stable"
date: 2007-12-26
forum: Debian
---

### Post by Elvish Legion on 2007-12-26
Is it safe to use the testing repos on etch? Or am I looking at breaking my system and should dl the testing disc (I tried a network install but it kept stalling)

---

### Post by b9anders on 2007-12-27
It's generally quite safe to use.

---

### Post by Bachstelze on 2007-12-27
Note, however, that it you have the tesing repositories in your sources.list, when you do an *apt-get upgrade*, all your packages will be upgraded to testing. If you just want to install a few packages from testing, it's better to download them from [http://packages.debian.org](http://packages.debian.org) and install them manually without modifying your sources.list.

---

### Post by p_quarles on 2007-12-27
There is also a way to modify your apt preferences such that you can use the testing repos alongside the stable repos, but still give priority to Etch packages. In other words, you'd be able to install Compiz, e.g., from Lenny, while still keeping the Etch package of something like Abiword or libc6.

Unfortunately, my reference for this method is on the Debian support forums, which are offline at the moment. I believe it was a sticky, though, so it should be easy for anyone to find once they're back up and running.

---

### Post by benuski on 2007-12-27
From what I know, its actually a bad idea to mix testing and stable, since they both use a different version of libc6.  If you need newer stuff, try backports.org, or just upgrade all the way to lenny... its about as stable as any Ubuntu release is.

---

### Post by p_quarles on 2007-12-27
Found another version of the guide to maintaining a mixed system. It's definitely not for mission-critical systems, but it allows you to keep one distro as the default while still enabling the repositories from Testing or Unstable. 
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

---

### Post by kellemes on 2008-01-02
And another link.. works pretty fine when you get the hang of it.
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

---

