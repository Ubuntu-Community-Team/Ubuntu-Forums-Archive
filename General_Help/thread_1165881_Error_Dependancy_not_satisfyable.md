---
title: "Error: Dependancy not satisfyable"
date: 2009-05-21
forum: General Help
---

### Post by dai_vernon on 2009-05-21
I am trying to install Astromenace, a game available in binary or source for linux.  Development appears to have stopped, and it looks to depend on a library that is not in modern repos:  libopenal0a. It is referenced in the Jaunty repos but the newer version of the install candidate does not satisfy the dependency.  Is there a way I can get around this or am I screwed?

---

### Post by Yellow Pasque on 2009-05-21
This should work:
[http://packages.ubuntu.com/hardy/libopenal0a](http://packages.ubuntu.com/hardy/libopenal0a)

---

### Post by mc4man on 2009-05-21
You can take this as you may, not a recommendation per se.

If  it was me I'd try one of 2 things

First I'd go here, download the .deb and see what Gdebi does and says. ( it 'appears' to be a 'standalone' lib, only dependent on an equal or greater version of libc6 (and you easily satisfy the 'greater'

[http://packages.ubuntu.com/hardy/libopenal0a](http://packages.ubuntu.com/hardy/libopenal0a)

If that seemed inappropriate or not possible, then I'd probably dl the source file, and see if it could be built. (  though I'd certainly refrain from changing any existing jaunty packages to satisfy build deps

---

### Post by dai_vernon on 2009-05-21
Thanks, both of you.  I had already tried building from source but there was no makefile and I didn't care enough to try and generate one.  I downloaded the hardy package and everything works now.  I was scared to try that because of Randall Munroe's story on the XKCD blog about his install getting so screwed up by installing from a repo that wasn't meant for his distro, but I guess one package isn't going to set anything on fire.

Great game by the way, check it out.

---

### Post by Yellow Pasque on 2009-05-21
Generally, installing from repos meant for other distros is a good way to get yourself in trouble. It's even worse when a n00b is determined to install a package that's incompatible with major packages in his system and uses the --force option, uninstalling most/all of the packages in his system.

However, I checked that this particular package's dependencies were satisfied.

---

