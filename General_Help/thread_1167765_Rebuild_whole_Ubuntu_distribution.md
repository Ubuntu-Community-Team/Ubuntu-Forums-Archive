---
title: "Rebuild whole Ubuntu distribution"
date: 2009-05-23
forum: General Help
---

### Post by _tomcio on 2009-05-23
Hello!

Ubuntu is optimized for i386, ok I understand this, backward compatibility is important. But since gcc 4.4 is out optimizing for specific platform can give really good performance boost.

So I'd like to know how Ubuntu build process looks like (we have access to whole Ubuntu sources, right?). I can repeat this process and focus more attention on optimization. Maybe there's already such project, I haven't found anything. Beside apt-build, but I don't believe, that it will successfully rebuild whole system for me...

I used Gentoo, but it takes too much time to maintenance it, I prefer Ubuntu.

---

### Post by sdennie on 2009-05-23
You can use apt-build to do this.  It might speed up a few applications but, in general, your applications aren't CPU bound and so compiling them with something more than -O2 probably won't make a difference (and may even have the opposite effect).

---

