---
title: "zsnes out of the repos?"
date: 2010-02-15
forum: Gaming &amp; Leisure
---

### Post by swoll1980 on 2010-02-15
Did they take it out of the repos, or am I just doing something wrong?
when I try to install I get this message. 

Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

When I do an apt-cache search I get nothing.

---

### Post by cbwcjw on 2010-02-15
[http://packages.ubuntu.com/search?keywords=zsnes](http://packages.ubuntu.com/search?keywords=zsnes)

It's there. Make sure your universe repository is enabled, system -> administration -> software sources.

Or better yet,
```
sudo apt-get clean
```
```
sudo apt-get update
```

---

### Post by DoktorSeven on 2010-02-16
Well, if you look at the details on that site, you'll see it's i386 only.  If the original poster uses amd64, it won't be in the repos.

It might be possible to download the .deb package from that site for his version of Ubuntu and use --force-architecture in dpkg to install, as long as he has the 32bit libs installed.

---

### Post by swoll1980 on 2010-02-16
> **DoktorSeven said:**
> Well, if you look at the details on that site, you'll see it's i386 only.  If the original poster uses amd64, it won't be in the repos.

It might be possible to download the .deb package from that site for his version of Ubuntu and use --force-architecture in dpkg to install, as long as he has the 32bit libs installed.

I do have an amd64. I would have to say CRAP! and thank you for your helpful post. :)

---

