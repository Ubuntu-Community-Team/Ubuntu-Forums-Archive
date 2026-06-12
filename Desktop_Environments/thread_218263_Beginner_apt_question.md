---
title: "Beginner apt question"
date: 2006-07-18
forum: Desktop Environments
---

### Post by endfx on 2006-07-18
Hi,

Can I use apt to find out what version of a program I have?
This is for a server so I can't use synaptic as I only have a command line.

Can apt list the package versions I have installed?

And I did look at the debian apt manual, but I couldn't find this information in it.

---

### Post by wahman143 on 2006-07-18
Hi,
[http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html)

I think this may be what you're looking for - 

apt-cache show <pkg_name>

HTH,
Wah

---

### Post by Stemp on 2006-07-18
apt-cache search searchname
apt-cache policy packagename

---

### Post by etank on 2006-07-18
Use ```
dpkg -l | grep *appname*
```That will tell you what version of the app is installed on your machine using ```
apt-cache search
``` or ```
apt-cache show
```tels you what is in the repos.

---

### Post by endfx on 2006-07-18
Thanks etank!

yeah apt-cache show and apt-cache search are for all package names, not just what I've installed.

dpkg -l works great.

---

### Post by endfx on 2006-07-18
dpkg -l gives you status codes in the first column.
Can you tell me what ii and rc status codes mean?

They sure are not documented in the man pages, which they really should be.

---

