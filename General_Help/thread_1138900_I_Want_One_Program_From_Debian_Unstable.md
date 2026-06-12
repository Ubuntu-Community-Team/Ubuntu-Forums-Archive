---
title: "I Want One Program From Debian Unstable"
date: 2009-04-26
forum: General Help
---

### Post by popejeremy on 2009-04-26
Hi. I'm using Ubuntu Jaunty, but there's *one* program that's in Debian Unstable and *only* in Debian Unstable that I want to get. The name of the program is fizmo.

For now, I've installed fizmo on my own without apt-get, but that's annoying as it doesn't automatically upgrade itself. How can I tell my Ubuntu to get this application and only this application from Debian Unstable?

---

### Post by steveneddy on 2009-04-26
How did you install it and from where did you get the download files?

---

### Post by kanikilu on 2009-04-26
I think you might be able to do that with [apt-pinning]("http://wiki.debian.org/AptPinning"), but I haven't actually used it myself, so maybe someone with more experience with it can give you a more definitive answer...

---

### Post by popejeremy on 2009-04-26
I went here [http://spellbreaker.org/~chrender/fizmo/](http://spellbreaker.org/~chrender/fizmo/) and downloaded the .deb file and did dpkg on it.

---

### Post by todak on 2009-04-26
In general, any apps that you install outside of the repositories must be updated manually. For instance, I use **stylus-toolbox** to report ink levels in my Epson Stylus C66 printer. I had to manually download and install it and I periodically check for update from the website, unless it ever appears in the Ubuntu repositories (hint, hint :)). I also use **cqrlog** for amateur radio logging and must also do the same for it.

---

